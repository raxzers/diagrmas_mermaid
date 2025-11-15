```mermaid
flowchart TD
    A[Inicio] --> B[Registrar handler SIGINT]
    B --> C[Abrir y cargar eBPF skeleton]
    C --> D[Adjuntar probes eBPF]
    D -->  G[Lanzar hilo stats_loop]
    G --> H[Crear ring buffer]
    H -->  J{Ejcución}
    J --> K[ring_buffer__poll]
    K --> L{¿Evento recibido?}
    L -- Sí --> M[Actualizar estadísticas]
    L -- No --> J
    M --> P[Acumular bytes en ventana]
   

    P --> J
    J -- Ctrl+C --> Q[Imprimir resumen]
    Q --> R[Cerrar CSV y liberar recursos]
    R --> S[Fin]
```
