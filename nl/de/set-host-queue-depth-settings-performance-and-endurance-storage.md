---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-17"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Empfehlungen für Einstellungen der Hostwarteschlangenlänge

Für jede Leistungsstufe wird eine maximale Länge für die Ein-/Ausgabewarteschlangen für den Host und die Anwendung empfohlen. Die Hosteinstellung wirkt sich nicht auf die Platten- und Controllerlatenz aus, sondern nur auf die Latenz, die für den Host und die Anwendung beobachtet wird.

<table align="center">
  <caption>Empfohlene Warteschlangenlänge für die einzelnen IOPS-Stufen</caption>
        <thead>
	    <tr>
		<th>Leistungsstufe</th>
		<th>Maximale Länge der Hostwarteschlange</th>
	    </tr>
	</thead>
	<tbody>
   	    <tr>
		<td style="text-align: center; vertical-align: middle;">0,25 IOPS pro GB</td>
		<td style="text-align: center; vertical-align: middle;">8</td>
	    </tr>
	    <tr>
		<td style="text-align: center; vertical-align: middle;">2 IOPS pro GB</td>
		<td style="text-align: center; vertical-align: middle;">24</td>
	    </tr>
	    <tr>
		<td style="text-align: center; vertical-align: middle;">4 IOPS pro GB</td>
		<td style="text-align: center; vertical-align: middle;">56</td>
            </tr>
         </tbody>
</table>

Eine Warteschlangenlänge über die empfohlenen Werte hinaus kann die E/A-Latenz erhöhen. Eine Warteschlangenlänge unter dem empfohlenen Wert kann möglicherweise die E/A-Leistung des Hosts verringern. Da jede Anwendung anders ist, sind Anpassungen und Beobachtungen erforderlich, um die maximale Speicherleistung zu erzielen.

Die Warteschlangenlänge des Hosts wird in der Regel im Hostbusadaptertreiber (host bus adapter) oder im Hypervisor und manchmal auch in der Anwendung angepasst. Standardwerte wie 32 oder 64 können eine übermäßige Latenz des Hosts oder der Anwendung zur Folge haben.

Wenn ein Host oder Hypervisor mehrere Leistungsstufen verwendet, verwenden Sie die Warteschlangenlänge für die schnellste Stufe und beobachten die Latenz auf der langsamsten Leistungsstufe. Wenn die Latenz auf der niedrigsten Stufe nicht akzeptabel ist, passen Sie die Warteschlangenlänge an, bis eine ausgeglichene Latenz und Leistung für alle Stufen zu beobachten ist.
