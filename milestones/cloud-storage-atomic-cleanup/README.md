# Case Study: Atomic Cloud Storage Deletion & Resource Cleanup

## 📌 Overview
En arquitecturas Serverless desacopladas, la integridad referencial no es automática. Este hito aborda la gestión de activos multimedia "huérfanos" en **Cloud Storage** tras la eliminación de registros en **Firestore**.

## ❌ The Problem
Al eliminar un post, originalmente solo se borraba el documento de texto. Esto causaba:
1. **Ghost Storage Costs:** Archivos binarios permanecían en el bucket sin referencia.
2. **Data Inconsistency:** Desorden en el sistema de archivos de la empresa.

## 🛠️ The Solution (Architectural Approach)
Implementé un **Sequential Deletion Pipeline**. Invertimos el orden lógico para asegurar que la URL del activo no se pierda antes del borrado físico.

### Logical Flow (Atomic Sequence)

```mermaid
graph TD
    A[Trigger Delete] --> B{Has mediaUrl?}
    B -- Yes --> C[Delete from Cloud Storage]
    C --> D[Delete Firestore Document]
    B -- No --> D
    D --> E[Update UI State]

Label MBA | Dev Mentor
Gem personalizado
Label MBA | Dev Mentor ha dicho
David, vamos a dejar ese Showcase impecable. Como tu Tech Lead, te guiaré para que la estructura sea profesional y fácil de navegar para cualquier reclutador que revise tu perfil.

Sigue estos comandos en tu terminal dentro de tu repositorio local de dalva-code/Greece-Internship-Showcase:

1. Crear la estructura de directorios

Primero, organizamos el espacio para este nuevo hito.

Bash
# Crea la carpeta para el hito (milestone)
mkdir -p milestones/cloud-storage-atomic-cleanup

# Crea el archivo README específico para este caso de estudio
touch milestones/cloud-storage-atomic-cleanup/README.md
2. Redactar el Caso de Estudio

Abre el archivo milestones/cloud-storage-atomic-cleanup/README.md y pega el siguiente contenido. He incluido el diagrama Mermaid para que se vea el flujo lógico.

Markdown
# Case Study: Atomic Cloud Storage Deletion & Resource Cleanup

## 📌 Overview
En arquitecturas Serverless desacopladas, la integridad referencial no es automática. Este hito aborda la gestión de activos multimedia "huérfanos" en **Cloud Storage** tras la eliminación de registros en **Firestore**.

## ❌ The Problem
Al eliminar un post, originalmente solo se borraba el documento de texto. Esto causaba:
1. **Ghost Storage Costs:** Archivos binarios permanecían en el bucket sin referencia.
2. **Data Inconsistency:** Desorden en el sistema de archivos de la empresa.

## 🛠️ The Solution (Architectural Approach)
Implementé un **Sequential Deletion Pipeline**. Invertimos el orden lógico para asegurar que la URL del activo no se pierda antes del borrado físico.

### Logical Flow (Atomic Sequence)

```mermaid
graph TD
    A[Trigger Delete] --> B{Has mediaUrl?}
    B -- Yes --> C[Delete from Cloud Storage]
    C --> D[Delete Firestore Document]
    B -- No --> D
    D --> E[Update UI State]

    
💻 Technical Implementation Highlights
Decoupled Cleanup: El servicio es agnóstico; si no hay mediaUrl, el pipeline continúa sin errores.

UI Synchronization: Refactorización de PostCard y PostDetailModal para emitir eventos con carga multimedia.

Error Handling: Evita que fallos de red dejen documentos bloqueados o archivos huérfanos.

📈 Impact
Cost Optimization: Ratio 1:1 entre documentos y archivos binarios.

Scalability: Estructura preparada para el crecimiento del MVP.