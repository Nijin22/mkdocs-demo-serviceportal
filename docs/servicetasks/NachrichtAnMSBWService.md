# NachrichtAnMSBWService

## Vollständiger Name

`de.seitenbau.serviceportal.prozess.servicetask.NachrichtAnMSBWService`

## Properties

| Name             | Pflicht | Beschreibung                                                 | Beispiel     | Default |
| ---------------- | ------- | ------------------------------------------------------------ | ------------ | ------- |
| empfaengerId     | ja      | IDP-Id des Empfängers                                        | ${startedBy} |         |
| senderId         | nein *  | IDP-Id des Senders                                           | ${startedBy} |         |
| betreff          | nein    | Subject der Nachricht                                        |              |         |
| text             | nein    | Text der Nachricht                                           |              |         |
| anhaenge         | nein    | Die Anhänge der Nachricht. Set, List, Array oder einzelnes Objekt der Klassen FormContent oder BinaryContent |              |         |
| saveToSentFolder | nein    | Gibt an, ob die Nachrich im Gesendet-Ordner des Senders gespeichert werden soll. |              | true    |
| language         | nein    | Sprache der Nachricht, de oder en oder fr                    |              | de      |

In Text und Betreff der Nachricht kann über den Platzhalter  {{LINK_AUF_AKTUELLEN_PROZESS}} ein Link zum Prozess zur Verfügung  gestellt werden.

## * senderId

Natürlich benötigt jede Nachricht einen Absender. Falls dieses Feld leer gelassen wird, so wird der in der Systemkonfiguration angegebene  Standartabsender verwendet. Die Kopie der Nachricht im Gesendet-Ordner  kann in diesem Fall nur über Zugang zu dem Standartkonto erreicht  werden, bzw. zukünftig wird je nach Konfiguration keine Kopie mehr  erstellt.

## Speicherlimits von Postfächern

Beim Versenden von Servicekonto-Nachrichten mittels dieses Servicetasks werden Speicherlimits **nicht** berücksichtigt, d.h.Nachrichten werden fehlerfrei versendet auch wenn beim Postfach des Absenders und/oder des Empfänger das Speicherlimit überschritten ist.

Siehe hierzu auch die [Hinweise zu Speicherplatzlimits bei Servicekonto-Postfächern](https://wiki.amt24.sachsen.de/bin/view/Übergreifendes/Speicherlimits im Servicekonto-Postfach/).

## Fehler beim Versenden von Nachrichten

Tritt beim Versenden einer Servicekonto-Nachricht ein Fehler auf, so erfolgt  ein Rollback zum letzten User-Task vor dem Service-Task. Der Benutzer,  der für diesen User-Task zuständig war, bekommt in diesem Fall das  entsprechende Formular mit einem generischen Hinweis angezeigt, dass ein Fehler aufgetreten ist. Weitere Prozessteilnehmer werden nicht  benachrichtigt.