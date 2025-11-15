```mermaid
flowchart TD
    A[Inicio] --> B[Registrar handler SIGINT]
    B --> C[Abrir y cargar eBPF skeleton]
    C --> D[Adjuntar probes eBPF]
    D -->  H[Crear ring buffer]
    H -->  J{Ejcución}
    J --> K[ring_buffer__poll]
    K --> L{¿Evento recibido?}
    L -- Sí --> M[Actualizar estadísticas]
    M -->  O[Imprimir y guardar en CSV]
    L -- No --> J
    O --> J
    J -- Ctrl+C --> Q[Imprimir resumen]
    Q --> R[Cerrar CSV y liberar recursos]
    R --> S[Fin]
```
