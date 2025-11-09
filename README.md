using System;
using System.Diagnostics;
using System.Threading;

namespace ProcessMonitorApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("=== System Process Monitor ===");
            while (true)
            {
                Console.Clear();
                Process[] processList = Process.GetProcesses();
                Console.WriteLine($"{"PID",-8} {"Process Name",-25} {"Memory (MB)",10}");
                Console.WriteLine(new string('-', 50));

                foreach (var proc in processList)
                {
                    try
                    {
                        Console.WriteLine($"{proc.Id,-8} {proc.ProcessName,-25} {(proc.WorkingSet64 / 1024 / 1024),10}");
                    }
                    catch { }
                }
                Thread.Sleep(3000);
            }
        }
    }
}
