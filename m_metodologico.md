sequenceDiagram
    actor Investigador
    participant eBPF as Módulo eBPF
    participant Kernel
    participant UserApp as User Space App
    participant CSV as Archivo CSV/Logs
    participant Tests as Plan de Pruebas

    %% Desarrollo
    Investigador ->> Investigador: Define protocolos, tracepoints y objetivos
    Investigador ->> eBPF: Implementa y compila el módulo
    eBPF ->> Kernel: Se carga en el Kernel

    %% Ejecución
    Kernel ->> eBPF: Genera eventos de lectura/escritura
    eBPF ->> UserApp: Envía datos vía perf_buffer/mapas
    UserApp ->> UserApp: Procesa métricas\n(calcula diferenciales)
    UserApp ->> CSV: Guarda resultados

    %% Validación
    Tests ->> UserApp: Ejecuta pruebas incrementales
    UserApp ->> Tests: Retorna métricas y resultados
    Investigador ->> Tests: Analiza resultados
    Tests ->> Investigador: Recomendaciones y ajustes

