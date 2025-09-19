@startuml
actor Investigador
participant "Módulo eBPF" as eBPF
participant Kernel
participant "User Space App" as UserApp
database "Archivo CSV/Logs" as CSV
participant "Plan de Pruebas" as Tests

== Desarrollo ==
Investigador -> Investigador: Define protocolos, tracepoints y objetivos
Investigador -> eBPF: Implementa y compila el módulo
eBPF -> Kernel: Se carga en el Kernel

== Ejecución ==
Kernel -> eBPF: Genera eventos de lectura/escritura
eBPF -> UserApp: Envía datos vía perf_buffer/mapas
UserApp -> UserApp: Procesa métricas\n(calcula diferenciales)
UserApp -> CSV: Guarda resultados

== Validación ==
Tests -> UserApp: Ejecuta pruebas incrementales
UserApp -> Tests: Retorna métricas y resultados
Investigador -> Tests: Analiza resultados
Tests -> Investigador: Recomendaciones/ajustes

@enduml
