## **Problema 271: Simulador del juego LCR**

### **Descripción**  
"LCR" (Left, Center, Right) es un juego de dados simple y divertido que se juega en grupo, donde cada jugador tiene una cantidad de fichas y sigue instrucciones basadas en los resultados de los dados para pasar fichas a otros jugadores o al centro. El objetivo es ser el último jugador con fichas restantes.

Escribe un algoritmo que simule el juego LCR, incluyendo a tres participantes: dos controlados por la computadora llamados Rosie y Bender, y un jugador humano cuyo nombre y cantidad de fichas inicial se solicitan al inicio.

---

### **Análisis**  
Para simular el juego "LCR" con tres participantes, se deben tener en cuenta las siguientes reglas y secuencias:

1. **Jugadores y Fichas Iniciales**:
   - El juego se desarrolla con tres jugadores: dos controlados por la computadora (Rosie y Bender) y un jugador humano.
   - Al inicio, se solicita el nombre del jugador humano y la cantidad de fichas iniciales, que debe estar entre 3 y 5.
      - Si el usuario ingresa un valor fuera del rango, se debe mostrar un mensaje de error y solicitar nuevamente hasta que se ingrese un número válido.
   - Todos los jugadores comienzan con la misma cantidad de fichas determinada al inicio.
   - El juego se desarrolla en turnos, donde cada jugador lanza los dados y sigue las instrucciones hasta que solo uno quede con fichas.

2. **Visualización del Estado del Juego Antes de Cada Turno**:
   - Antes de cada turno, el sistema muestra las posiciones relativas y cantidad de fichas de los jugadores con referencia únicamente al jugador que va a lanzar, junto con un mensaje claro sobre el jugador que está por lanzar:
     
     - Si el jugador humano va a lanzar:
       ```
       Turno de Humano:
       [Rosie: ? fichas] <-- [Humano: ? fichas] --> [Bender: ? fichas]
       Humano lanzará ? dados.
       ```

     - Si Rosie va a lanzar:
       ```
       Turno de Rosie:
       [Bender: ? fichas] <-- [Rosie: ? fichas] --> [Humano: ? fichas]
       Rosie lanzará ? dados.
       ```

     - Si Bender va a lanzar:
       ```
       Turno de Bender:
       [Humano: ? fichas] <-- [Bender: ? fichas] --> [Rosie: ? fichas]
       Bender lanzará ? dados.
       ```

3. **Lanzamiento de los Dados y Comportamiento de los Resultados**:
   - En cada turno, el jugador lanza entre uno y tres dados, dependiendo de la cantidad de fichas que tiene, y el sistema muestra un mensaje indicando el número de dados lanzados.
   - Los dados pueden mostrar las siguientes caras:
      - **1: L (Left)** - Pasa una ficha al jugador a la izquierda.
      - **2: C (Center)** - Coloca una ficha en el centro, eliminándola del juego.
      - **3: R (Right)** - Pasa una ficha al jugador a la derecha.
      - **4: 1 (Punto)** - Acción neutra, no se hace nada.
      - **5: 2 (Punto)** - Acción neutra, no se hace nada.
      - **6: 3 (Punto)** - Acción neutra, no se hace nada.
   - Si un jugador tiene menos de tres fichas, solo lanza la cantidad de dados equivalente al número de fichas que posee.
   - **Para el jugador humano**: El algoritmo debe solicitar que escriba la letra **"L"** para lanzar los dados. Si se ingresa cualquier otro valor, el sistema debe mostrar un mensaje de error y solicitar nuevamente la entrada hasta que sea correcta.

4. **Mensajes del Sistema Durante el Juego**:
   - Cada vez que un jugador lanza los dados, el sistema muestra un mensaje detallado de los resultados de los dados y las acciones realizadas.
     - Ejemplo: `"Humano lanzó 3 dados: L, •, R"`
     - `"Humano pasó 1 ficha a Rosie y 1 ficha a Bender"`
   - Al final de cada turno, el sistema muestra el estado actualizado de las fichas de cada jugador.

5. **Orden de los Jugadores y Sentido del Juego**:
   - El juego se desarrolla en sentido **horario**, comenzando siempre con el jugador humano, seguido de Rosie y, por último, Bender.
   - Este orden se repite cíclicamente hasta que solo uno de los tres conserve fichas.

6. **Estructura de Control para el Flujo de Turnos**:
   - Para manejar el flujo de turnos, el algoritmo debe utilizar una estructura de control iterativa del tipo **"Hacer... Repetir"** para verificar constantemente si se ha alcanzado la condición de finalización (solo un jugador conserva fichas).
   - No se pueden usar instrucciones rompedoras (como **romper**, **continuar** u otra similar) para finalizar el ciclo. La condición de finalización debe evaluarse directamente en la estructura "Hacer... Repetir".

7. **Objetivo del Juego**:
   - El juego continúa en rondas hasta que solo un jugador tenga fichas, convirtiéndose en el ganador.
   - Los jugadores que pierden todas sus fichas no lanzan los dados en su turno, pero pueden recibir fichas de otros jugadores y reintegrarse al juego.

**Ejemplo de desarrollo del juego**:  
1. Antes de comenzar el turno del jugador humano, el sistema muestra:

   ```
   Turno de Humano:
   [Rosie: 3 fichas] <-- [Humano: 3 fichas] --> [Bender: 3 fichas]
   Humano lanzará 3 dados.
   ```

2. El sistema solicita al jugador humano que escriba "L" para lanzar los dados. Si se ingresa otro valor, se muestra un mensaje de error y se solicita nuevamente hasta que sea correcto.
3. El jugador humano lanza tres dados y obtiene los resultados: `L`, `•`, `R`.
   - El sistema muestra: `"Humano lanzó 3 dados: L, •, R"`
   - También muestra las acciones: `"Humano pasó 1 ficha a Rosie y 1 ficha a Bender"`
4. Al final de cada turno, el sistema muestra el estado actualizado de las fichas de cada jugador y se verifica la condición de finalización.
5. El juego continúa en sentido horario hasta que solo un jugador tiene fichas, y ese jugador es el ganador.

---

### **Requerimientos**  
- El algoritmo debe solicitar el nombre del jugador humano al inicio del juego.
- El algoritmo debe solicitar la cantidad inicial de fichas, validando que esté entre 3 y 5. Si el usuario ingresa un valor fuera de este rango, se debe mostrar un mensaje de error y solicitar nuevamente hasta que sea correcto.
- Antes de cada turno, el sistema debe mostrar las posiciones relativas y la cantidad de fichas de los jugadores, con referencia únicamente al jugador que va a lanzar, junto con un mensaje claro sobre quién lanzará los dados y cuántos.
- Para lanzar el dado, el jugador humano debe escribir la letra **"L"**. Si se ingresa cualquier otro valor, el sistema debe mostrar un mensaje de error y solicitar nuevamente la entrada hasta que sea correcta.
- Cada vez que un jugador lanza los dados, el sistema debe mostrar un mensaje detallado de los resultados y las acciones realizadas en ese turno.
- El juego debe utilizar una estructura de control iterativa **"Hacer... Repetir"** para el flujo de turnos, sin emplear instrucciones rompedoras (como **romper**, **continuar** u otra similar) para finalizar el ciclo. La condición de finalización debe evaluarse directamente en la estructura.
- El juego se desarrolla en sentido **horario**, comenzando siempre con el jugador humano, seguido de Rosie y, por último, Bender.
- Cada jugador debe seguir las instrucciones de los dados en cada turno para pasar fichas o eliminarlas.
- Si un jugador tiene menos de tres fichas, solo debe lanzar el número de dados equivalente a la cantidad de fichas que posee.
- Los jugadores sin fichas no lanzan dados, pero pueden recibir fichas de otros jugadores y reintegrarse al juego.
- El juego debe finalizar cuando solo un jugador conserva fichas, declarando a ese jugador como el ganador.