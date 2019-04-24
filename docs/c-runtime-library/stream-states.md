---
title: Stavy proudu
ms.date: 11/19/2018
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
ms.openlocfilehash: f725fa16e8d669975dbc02c6eefd727085bbeb7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304716"
---
# <a name="stream-states"></a>Stavy proudu

Na následujícím obrázku jsou uvedeny platné stavy a přechody stavu pro datový proud.

![Diagram stavu Stream](../c-runtime-library/media/stream.gif "diagramu stavu Stream")

Každý z kruhů označuje stabilního stavu. Každý řádek znamená přechod, který může nastat v důsledku volání funkce, která pracuje v datovém proudu. Pět skupin funkce může způsobit přechodů mezi stavy.

Funkce v prvních tří skupin, které jsou deklarovány v \<stdio.h >:

- Číst bajt funkce – [fgetc –](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fread –](../c-runtime-library/reference/fread.md), [fscanf –](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc](../c-runtime-library/reference/getc-getwc.md), [ GetChar](../c-runtime-library/reference/getc-getwc.md), [získá](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), a [ungetc –](../c-runtime-library/reference/ungetc-ungetwc.md)

- Bajt napsat funkce – [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc](../c-runtime-library/reference/fputc-fputwc.md), [fputs –](../c-runtime-library/reference/fputs-fputws.md), [fwrite –](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc](../c-runtime-library/reference/putc-putwc.md), [putchar](../c-runtime-library/reference/putc-putwc.md), [vloží](../c-runtime-library/reference/puts-putws.md), [vfprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), a [vprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)

- Funkce pozice – [fflush –](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos](../c-runtime-library/reference/fsetpos.md), a [rewind](../c-runtime-library/reference/rewind.md)

Funkce v zbývající dvě skupiny jsou deklarovány v \<wchar.h >:

- Úrovni čtení funkce – [fgetwc –](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws –](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf –](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc –](../c-runtime-library/reference/getc-getwc.md), [getwchar –](../c-runtime-library/reference/getc-getwc.md), [ungetwc –](../c-runtime-library/reference/ungetc-ungetwc.md), a [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),

- Zápis úrovni funkce – [fwprintf –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc –](../c-runtime-library/reference/fputc-fputwc.md), [fputws –](../c-runtime-library/reference/fputs-fputws.md), [putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), a [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),

Stav diagram znázorňuje, musí volat jednu z funkcí pozice mezi většina operací čtení a zápisu:

- Čtení funkci nelze volat, pokud byla poslední operace v datovém proudu pro zápis.

- Zápis funkce nelze volat Pokud byla poslední operace v datovém proudu pro čtení, pokud není, přečtěte si, že operace nastaven indikátor konce souboru.

Nakonec diagramu stavu ukazuje operaci pozice nikdy snižuje počet volání platná funkce, která můžete postupovat podle.

## <a name="see-also"></a>Viz také:

[Soubory a proudy](../c-runtime-library/files-and-streams.md)
