---
title: Textové a binární proudy
ms.date: 11/04/2016
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: a47c0b79b10f685c1f43ae4bfbfc6e1b9ea2b508
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664903"
---
# <a name="text-and-binary-streams"></a>Textové a binární proudy

Textového datového proudu se skládá z jednoho nebo více řádků textu, který je možné zapisovat na zobrazení orientovaný text tak, že budou moct přečíst. Při čtení z textového datového proudu, program přečte `NL` (nový řádek) na konci každého řádku. Při zápisu do proudu textu, program zapíše `NL` který signalizuje, že konec řádku. Tak, aby odpovídaly různý konvence mezi cílových prostředí pro vyjádření text v souborech, můžete změnit funkce knihovny číslo a reprezentace znaků přenášet mezi aplikací a textového datového proudu.

Umístění v rámci textového datového proudu je proto omezena. Aktuální indikátor pozice v souboru lze získat voláním [fgetpos](../c-runtime-library/reference/fgetpos.md) nebo [ftell –](../c-runtime-library/reference/ftell-ftelli64.md). Textového datového proudu můžete umístit na pozici získat tímto způsobem, nebo na začátku nebo konci datového proudu, voláním [fsetpos](../c-runtime-library/reference/fsetpos.md) nebo [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Změna umístění nemusí být také podporován.

Pro zajištění maximální přenositelnosti by neměl napsat program:

- Prázdné soubory.

- Znaky mezery na konci řádku.

- Částečné řádky (vynecháním `NL` na konci souboru).

- jiné znaky než tisknutelné znaky, NL, a `HT` (horizontální tabelátor).

Pokud budete postupovat podle těchto pravidel, posloupnost znaků, které čtení z textového datového proudu (buď jako bajt nebo vícebajtové znaky) bude odpovídat posloupnost znaků, který jste napsali textového datového proudu při vytváření souboru. Funkce knihovny v opačném případě můžete odebrat soubor, který vytvoříte, je-li soubor je prázdný, pokud ho zavřete. Nebo můžete změnit ani odstranit znaků, které můžete zapisovat do souboru.

Binární datový proud se skládá z jednoho nebo více bajtů libovolné informace. Můžete napsat hodnotu uloženou v objektu libovolného k binárnímu proudu (byte objektově orientovaný) a číst přesně co byla uložena v objektu při jste napsali. Funkce knihovny nemění bajtů, které přenášejí mezi aplikací a do binárního datového proudu. Libovolný počet bajty s hodnotou null, však může připojit k souboru, který píšete do binárního datového proudu. Program musí řešit tyto další bajty s hodnotou null na konci binární datový proud.

Umístění v rámci binárnímu datovému proudu je proto dobře definované, s výjimkou umístění vzhledem k konce datového proudu. Můžete získat a změnit aktuální indikátor pozice v souboru je stejný jako u textového datového proudu. Kromě toho používá posunutí [ftell –](../c-runtime-library/reference/ftell-ftelli64.md) a [fseek](../c-runtime-library/reference/fseek-fseeki64.md) počet bajtů od začátku datového proudu (což je nula bajtů), takže vrací celé číslo aritmetické na tyto hodnoty posunu předvídatelné výsledky.

Datový proud bajtů zpracovává soubor jako sekvence bajtů. V rámci programu datového proudu vypadá jako stejnou sekvenci bajtů, s výjimkou případné změny, které je popsáno výše.

## <a name="see-also"></a>Viz také

[Soubory a proudy](../c-runtime-library/files-and-streams.md)