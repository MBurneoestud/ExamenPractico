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
Acción/datos, esperado y observado ANTES: entrar a la pagina avistamientos, deberia mostrar la lista de avistamientos con el nombre de la criatura. No muestra el nombre, muestra el ID de la criatura. Evidencia visible en EVIDENCIA-A02-FRONT

### Causa
Explicación causal y archivo/capa, no solo su nombre: funcion async en capa services no esta mandando populate, por lo que solo devuelve el ID. Funcion listar de avistamientos.service.ts, linea 12. Evidencia visible en EVIDENCIA-A02-SERVICE

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección: funcion async listar de avistamiento.service.ts, agregada linea a seccion de return. Hace que Mongoose no devuelva solo el ID, pero tambien el nombre de la criatura. REACT ya tiene capacidad de leer y mostrar el nombre, pero requiere de Mongoose para obtener l nombre y no solo ID. Commit: "Agregada linea 13 .populate para resolver problema de funcion de listado A02"

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia: Bajar backend, volver a correr con npm run dev, entrar a pagina avistamientos. Lista deberia mostrar avistamientos con el nombre de la criatura como se ve en EVIDENCIA-A02-FRONT-ARREGLADO 

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta: Resuelto

## A-03 · Se acepta un peligro inválido
### Síntoma
Acción/datos, esperado y observado ANTES: Abrir Thunder Client, mandar un PUT con cualquier ID de criatura, agregar {"nivelPeligro":999} en JSON y aplastar send. Se recibe status 200 y la ventana response muestra el peligro sobre 10. Evidencia en EVIDENCIA-A03-THUNDER
### Causa
Explicación causal y archivo/capa, no solo su nombre: Problema de service y validacion, criaturas.service.ts no llama activa validacion cuando se usa findByIdandUpdate, validacion.ts no limita nivelPeligro a un rango 1-10

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección: Cambios en service y validacion, service activala validacion, la validacion ahora tiene una condicion que nivelPeligro debe ser un valor mayor a 1 pero maximo 10. Commit: "Guardando registro de evidencias y cambios para resolver A03. Tambien incluye formateado de archivos en el front"

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia: Abrir thunder, tratar PUT con numero invalido en el JSON, debe devolver 400. Tratar con numero valido, devuelve 200. Si se trata un GET despues de mandar valor invalido el JSON muestra el ultimo valor valido ingresado. Evidencia: capturas con A03 marcadas ARREGLADO

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta: Resuelto

## A-04 · El filtro no actualiza la pantalla
### Síntoma
Acción/datos, esperado y observado ANTES: Se entra a la pagina criaturas, se selecciona mitica y luego mecanica pero no se aplasta actualizar, la lista no refleja la categoria seleccionada como se ve en EVIDENCIA-A04-FRONT

### Causa
Explicación causal y archivo/capa, no solo su nombre: ListaCriaturas.tsx, el efecto iniciado en la linea 12 solo depende de recarga, por lo que cambiar el selector de categoria no lanza la consulta que cambiaria el listado. Problema esta en linea 30, despues del cierre del efecto, como se ve en EVIDENCIA-A04-LISTA

### Cambio
Qué modifiqué, por qué resuelve la causa y commit de corrección: agregado "tipo" al cierre del efecto problematico en ListaCriaturas.tsx en la linea 30. Esto hace que cada cambio de selector vuelva a ejecutar la funcion listarCriaturas(tipo). Commit :"Arreglado problema A04, localizado en ListaCriaturas.tsx. Agregadas evidencias y actualizado documento de auditoria"

### Prueba
Pasos/comando, datos, status/resultado esperado y observado DESPUÉS; archivo de evidencia: Volver a cargar pagina criaturas en el front, cambiar de selectores sin aplastar el boton actualizar. Cada cambio de selector deberia devolver las criaturas correspondientes a ese tipo, o no hay resultados si el tipo no tiene criaturas registradas. Consultar evidencias con nombres A04 y ARREGLADO

### Estado
Resuelto / parcial / no resuelto. Si es parcial, qué falta: Resuelto

