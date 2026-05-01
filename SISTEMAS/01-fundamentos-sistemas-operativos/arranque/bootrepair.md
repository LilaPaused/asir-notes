# Boot Repair

## Qué es

Boot Repair es una herramienta gráfica que permite reparar problemas de arranque en sistemas Linux y dual boot.

Es útil cuando GRUB no aparece o cuando Windows ha sobrescrito el gestor de arranque.

## Caso típico

Una máquina virtual tiene:

- disco con Windows
- disco con Ubuntu

Pero no aparece un gestor de arranque funcional.

## Procedimiento general

1. Montar la ISO de Boot Repair.
2. Arrancar la máquina desde esa ISO.
3. Elegir Boot Repair.
4. Usar opciones avanzadas si hace falta.
5. Aplicar reparación.
6. Reiniciar.
7. Comprobar que aparece GRUB.

## Uso básico

Normalmente basta con usar la reparación recomendada.

Si se quiere revisar, entrar en opciones avanzadas y aplicar.

## Resultado esperado

Después de reparar, GRUB debería mostrar entradas como:

- Ubuntu
- Advanced options for Ubuntu
- Windows 10

## Ventajas

- Es más rápido que reparar GRUB manualmente.
- Es útil en exámenes o prácticas con poco tiempo.
- Detecta problemas típicos de arranque.

## Desventajas

- No enseña tanto como hacerlo manualmente.
- Puede ocultar qué cambios concretos ha realizado.
- No siempre resuelve configuraciones raras.

## Cuándo usarlo

Usarlo cuando:

- GRUB no aparece.
- Windows arranca directamente.
- Linux existe pero no se puede seleccionar.
- Se necesita una solución rápida.

## Cuándo hacerlo manual

Mejor reparar manualmente cuando:

- quieres aprender bien el proceso
- Boot Repair falla
- necesitas controlar particiones EFI
- hay varios discos o configuraciones complejas

## Conceptos relacionados

- [GRUB](./grub.md)
- [Reparar GRUB manualmente](./reparar-grub.md)
