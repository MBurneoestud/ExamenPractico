# Auditoría · Versión A
Código: 00338148
Repositorio público propio: https://github.com/MBurneoestud/ExamenPractico.git
Rama: examen/338148

## A-01 · No se registra el avistamiento
### Síntoma
Acción/datos, esperado y observado ANTES: Intento de registrar nuevo avistamiento, see llenan los campos con cualquier criatura ya registrada. Al aplastar boton "guardar" no se registra, manda mensaje visible en imagen: EVIDENCIA-A01-FRONT.png

### Causa
Explicación causal y archivo/capa, no solo su nombre: Frontend - FormularioAvistamiento.tsx arma nombre incorrecto al guardar el avistamiento
Backend - avistamiento.service.ts y validacion.ts | El service no tiene "criaturaId" como campo valido (linea 5), la validacion lo rechaza por no ser valido, produce mensaje de error

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección: Cambio en linea 82 de FormularioAvistamiento.tsx, resuelve el conflicto de campos entre formulario y service. Commit "Cambio en linea 82, arregla problema A01, resolviendo conflicto de campos entre form y service"

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia: Repetir intento de registrar avistamiento con cualquier criatura, llenar todos los campos del formulario, guardar. Debe no devolver ningun error como muestra captura de pantalla EVIDENCIA-A01-FORM-ARREGLADO

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta: Resuelto

## A-02 · La lista no identifica a la criatura
### Síntoma
Acción/datos, esperado y observado ANTES:

### Causa
Explicación causal y archivo/capa, no solo su nombre:

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección:

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia:

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta:

## A-03 · Se acepta un peligro inválido
### Síntoma
Acción/datos, esperado y observado ANTES:

### Causa
Explicación causal y archivo/capa, no solo su nombre:

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección:

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia:

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta:

## A-04 · El filtro no actualiza la pantalla
### Síntoma
Acción/datos, esperado y observado ANTES:

### Causa
Explicación causal y archivo/capa, no solo su nombre:

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección:

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia:

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta:

