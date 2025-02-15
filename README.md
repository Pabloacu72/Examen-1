# Examen-1
Examen 1
[examen javier gonzalez pablo acuña.pdf](https://github.com/user-attachments/files/18812978/examen.javier.gonzalez.pablo.acuna.pdf)


using System;

namespace examennnn
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Definir variables para empleados
            string empleado1 = "Cajero";
            string empleado2 = "Gerente";
            string empleado3 = "Operario";

            double tarifaCajero = 5.0;
            double tarifaGerente = 10.0;
            double tarifaOperario = 7.0;

            int horasTrabajadasCajero = 0, horasTrabajadasGerente = 0, horasTrabajadasOperario = 0;
            int faltasCajero = 0, faltasGerente = 0, faltasOperario = 0;
            int retrasosCajero = 0, retrasosGerente = 0, retrasosOperario = 0;

            double bono = 20.0;
            int maxHorasSemana = 40;
            int minHorasDia = 4;
            int maxHorasDia = 10;
            int maxRetrasos = 3;
            double recargoHorasExtra = 1.5;
            double descuentoObligatorio = 0.10; // 10% de deducción

            // Simulación de datos de entrada
            int entradaCajero = 9, salidaCajero = 17;
            int entradaGerente = 8, salidaGerente = 18;
            int entradaOperario = 10, salidaOperario = 19;

            // Cálculo de horas trabajadas para cada empleado (valida si no hay error en hora de salida)
            if (salidaCajero > entradaCajero) horasTrabajadasCajero = salidaCajero - entradaCajero;
            else Console.WriteLine("Error: Hora de salida inválida para Cajero");

            if (salidaGerente > entradaGerente) horasTrabajadasGerente = salidaGerente - entradaGerente;
            else Console.WriteLine("Error: Hora de salida inválida para Gerente");

            if (salidaOperario > entradaOperario) horasTrabajadasOperario = salidaOperario - entradaOperario;
            else Console.WriteLine("Error: Hora de salida inválida para Operario");

            // Validación de horas mínimas y máximas por día
            if (horasTrabajadasCajero < minHorasDia)
            {
                Console.WriteLine("Error: El Cajero no trabajó el mínimo de horas al día.");
            }

            if (horasTrabajadasCajero > maxHorasDia)
            {
                Console.WriteLine("Error: El Cajero excedió el máximo de horas al día.");
            }

            if (horasTrabajadasGerente < minHorasDia)
            {
                Console.WriteLine("Error: El Gerente no trabajó el mínimo de horas al día.");
            }

            if (horasTrabajadasGerente > maxHorasDia)
            {
                Console.WriteLine("Error: El Gerente excedió el máximo de horas al día.");
            }

            if (horasTrabajadasOperario < minHorasDia)
            {
                Console.WriteLine("Error: El Operario no trabajó el mínimo de horas al día.");
            }

            if (horasTrabajadasOperario > maxHorasDia)
            {
                Console.WriteLine("Error: El Operario excedió el máximo de horas al día.");
            }

            // Aplicación de penalizaciones por retrasos
            if (retrasosCajero > maxRetrasos) horasTrabajadasCajero -= 1;
            if (retrasosGerente > maxRetrasos) horasTrabajadasGerente -= 1;
            if (retrasosOperario > maxRetrasos) horasTrabajadasOperario -= 1;

            // Cálculo del salario bruto
            double salarioBrutoCajero = horasTrabajadasCajero * tarifaCajero;
            double salarioBrutoGerente = horasTrabajadasGerente * tarifaGerente;
            double salarioBrutoOperario = horasTrabajadasOperario * tarifaOperario;

            // Aplicación de bonos si no hay faltas
            if (faltasCajero == 0) salarioBrutoCajero += bono;
            if (faltasGerente == 0) salarioBrutoGerente += bono;
            if (faltasOperario == 0) salarioBrutoOperario += bono;

            // Aplicación de horas extras si se excede el máximo de horas semanales
            if (horasTrabajadasCajero > maxHorasSemana)
                salarioBrutoCajero += (horasTrabajadasCajero - maxHorasSemana) * tarifaCajero * recargoHorasExtra;

            if (horasTrabajadasGerente > maxHorasSemana)
                salarioBrutoGerente += (horasTrabajadasGerente - maxHorasSemana) * tarifaGerente * recargoHorasExtra;

            if (horasTrabajadasOperario > maxHorasSemana)
                salarioBrutoOperario += (horasTrabajadasOperario - maxHorasSemana) * tarifaOperario * recargoHorasExtra;

            // Aplicación de deducciones
            double deduccionCajero = salarioBrutoCajero * descuentoObligatorio;
            double deduccionGerente = salarioBrutoGerente * descuentoObligatorio;
            double deduccionOperario = salarioBrutoOperario * descuentoObligatorio;

            // Cálculo del salario neto
            double salarioNetoCajero = salarioBrutoCajero - deduccionCajero;
            double salarioNetoGerente = salarioBrutoGerente - deduccionGerente;
            double salarioNetoOperario = salarioBrutoOperario - deduccionOperario;

            // Mostrar resultados
            Console.WriteLine("Empleado: " + empleado1 + " | Salario Neto: $" + salarioNetoCajero);
            Console.WriteLine("Empleado: " + empleado2 + " | Salario Neto: $" + salarioNetoGerente);
            Console.WriteLine("Empleado: " + empleado3 + " | Salario Neto: $" + salarioNetoOperario);
        }
    }
}
