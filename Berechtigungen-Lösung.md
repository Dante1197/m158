### Ordnerstruktur erstellen:

1. Öffnen Sie die Eingabeaufforderung als Administrator.
2. Verwenden Sie die folgenden Befehle, um die Ordnerstruktur zu erstellen:

```plaintext
mkdir C:\Mittelerde
mkdir C:\Mittelerde\Völker
mkdir C:\Mittelerde\Völker\Zwerge
mkdir C:\Mittelerde\Völker\Elben
mkdir C:\Mittelerde\Völker\Menschen
```
### Gruppe erstellen und Vererbung erkennen:

1. Fügen Sie die Gruppe "Menschen" zum Ordner "C:\Mittelerde" hinzu:

```plaintext
icacls "C:\Mittelerde" /inheritance:r
icacls "C:\Mittelerde" /grant "Menschen":(OI)(CI)F
```
2. Nachdem die Gruppe "Menschen" dem Ordner "Mittelerde" hinzugefügt wurde und die Vererbung für "Mittelerde" deaktiviert wurde, erben die Unterordner "Völker", "Elben", "Menschen" und "Zwerge" nicht automatisch die Berechtigungen der übergeordneten Ebene "Mittelerde". Stattdessen werden möglicherweise spezifische Berechtigungen für jeden dieser Ordner festgelegt, je nachdem, ob bereits Berechtigungen explizit festgelegt wurden.
   
3. "Mittelerde" erbt standardmäßig seine Berechtigungen vom übergeordneten Ordner, wahrscheinlich dem Stammverzeichnis des Laufwerks "C:".

4. Wenn Sie die Vererbung für "Mittelerde" deaktivieren, erbt "Völker" keine Berechtigungen mehr automatisch von "Mittelerde".

5. Wenn Sie die Vererbung für "Mittelerde" deaktivieren, ändert sich die Vererbung der Berechtigungen für "Elben", "Menschen" und "Zwerge" nicht sofort. Sie erben weiterhin ihre Berechtigungen von "Völker", es sei denn, die Vererbung für "Völker" wird ebenfalls deaktiviert.

### Vererbungskette erkennen:

1.  Standardmäßig erben "Elben", "Menschen" und "Zwerge" die Berechtigungen von "Völker".
2. "Völker" erbt standardmäßig Berechtigungen von "Mittelerde".

### Auswirkungen beim deaktivieren von Vererbungen verstehen:

1. Wenn Sie die Vererbung auf **"Mittelerde"** deaktivieren, erben **"Völker"**, **"Elben"**, **"Menschen"** und **"Zwerge"** keine Berechtigungen mehr von **"Mittelerde"**. Es ändert sich nichts bei den Berechtigungen der Unterordner.
2. Um die Gruppe **"Menschen"** bei **"Elben"** und **"Zwerge"** zu entfernen, müssen Sie die Berechtigungen für diese Ordner anpassen:

```plaintext
icacls "C:\Mittelerde\Völker\Elben" /remove "Menschen"
icacls "C:\Mittelerde\Völker\Zwerge" /remove "Menschen"
```

3. Wenn Sie die Vererbung auf einem Ordner deaktivieren, erhalten Sie die Optionen, ob Sie die vorhandenen Berechtigungen behalten möchten (Option "Convert inherited permissions into explicit permissions") oder ob Sie die Berechtigungen des Ordners auf die Standardberechtigungen zurücksetzen möchten (Option "Remove all inherited permissions from this object").

4. Im GUI von Windows können Sie sehen, von wo ein Ordner seine Berechtigungen erbt, indem Sie die Eigenschaften des Ordners aufrufen und den Reiter "Sicherheit" öffnen. Dort finden Sie eine Liste der Berechtigungen und deren Herkunft.

5. Das Deaktivieren der Vererbung bei **"Mittelerde"** entfernt die Gruppe **"Menschen"** nicht von **"Elben"** und **"Zwerge"**, da die Berechtigungen für diese Ordner bereits explizit festgelegt wurden. Das Deaktivieren der Vererbung verhindert lediglich das automatische Aktualisieren der Berechtigungen basierend auf dem übergeordneten Ordner. Sie müssen die Berechtigungen für **"Elben"** und **"Zwerge"** explizit ändern, um die Gruppe **"Menschen"** zu entfernen.