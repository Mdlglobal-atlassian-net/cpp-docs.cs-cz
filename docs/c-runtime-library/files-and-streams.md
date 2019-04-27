---
title: Soubory a proudy
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
ms.openlocfilehash: ea11ea76ade8a68c2d8a92e08d3652035c996d3d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343742"
---
# <a name="files-and-streams"></a>Soubory a proudy

Aplikace komunikuje s cílového prostředí tak, že čtení a zápis do souborů. Soubor může být:

- Datové sady, který může číst a zapisovat opakovaně.

- Datový proud bajtů generovaných programu (například kanál).

- Datového proudu bajtů přijatých z nebo odesílat periferní zařízení.

Poslední dvě položky jsou interaktivní soubory. Soubory jsou obvykle hlavní prostředky k interakci s programem. Zpracování všech těchto typů souborů téměř stejným způsobem – voláním funkce knihovny. Můžete zahrnout standardní hlavička STDIO. H, chcete-li deklarovat většina těchto funkcí.

Abyste mohli provádět mnoho operací u souboru, musíte soubor otevřít. Otevření souboru přidruží k němu datový proud, do datové struktury v rámci standardní knihovny jazyka C, který glosses přes spoustu rozdílů mezi soubory různých druhů. Knihovny udržuje stav jednotlivých datových proudech v objektu typu souboru.

Cílové prostředí otevře tři soubory před spuštěním programu. Můžete otevřít soubor voláním funkce knihovny [fopen _wfopen –](../c-runtime-library/reference/fopen-wfopen.md) se dvěma argumenty. ( `fopen` Funkce se již nepoužívá, použijte [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) místo.) Prvním argumentem je název souboru. Druhý argument je řetězec C, který určuje:

- Určuje, zda máte v úmyslu číst data ze souboru nebo zapisovat data nebo obojí.

- Určuje, zda chcete generovat nový obsah souboru (nebo vytvořit soubor, pokud neexistuje dříve) nebo ponechat existující obsah na místě.

- Zápisy do souboru Určuje, zda lze měnit existující obsah nebo by měla pouze připojení bajtů na konci souboru.

- Určuje, zda chcete pracovat s textového datového proudu nebo binární datový proud.

Jakmile je soubor úspěšně otevřen, můžete určit, zda je datový proud bajtů orientovaný (datový proud bajtů) nebo široké orientovaný (wide datový proud). Datový proud je zpočátku nevázaného. Volání některých funkcí ovládajících datový proud díky bajtů orientovaný, zatímco některé funkce usnadňují široké orientovaný. Po vytvoření datového proudu udržuje jeho orientaci, dokud není zavřena voláním [fclose –](../c-runtime-library/reference/fclose-fcloseall.md) nebo [freopen](../c-runtime-library/reference/freopen-wfreopen.md).

© 2001 1989 podle P.J. Plauger a Jim Brodie. Všechna práva vyhrazena.

## <a name="see-also"></a>Viz také:

[Textové a binární proudy](../c-runtime-library/text-and-binary-streams.md)<br/>
[Bajtové a široké proudy](../c-runtime-library/byte-and-wide-streams.md)<br/>
[Řídicí proudy](../c-runtime-library/controlling-streams.md)<br/>
[Stavy proudu](../c-runtime-library/stream-states.md)
