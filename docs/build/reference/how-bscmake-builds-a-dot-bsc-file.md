---
title: 'Postupy: Sestavení souboru BSC programem BSCMAKE'
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: e691e6ee2dcda0fb04735705078f1ed2ff139301
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425585"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Postupy: Sestavení souboru BSC programem BSCMAKE

BscMake – sestavení nebo znovu sestaví souboru .BSC nástrojem nejefektivnějším způsobem, může to. Aby nedocházelo k problémům, je důležité pochopit, proces sestavení.

Při sestavení BSCMAKE informačního souboru procházení, zkrátí soubory .sbr délku nula. Soubor .sbr nulové délky (nebo je prázdný) říká během další sestavení na stejný soubor, BSCMAKE, že soubor .sbr nemá žádný nový příspěvek provést. Umožňuje BSCMAKE vědět, že aktualizace z část souboru se nevyžaduje a přírůstkového sestavení bude stačit. Při každém sestavení (Pokud je zadána možnost /n), BSCMAKE poprvé pokusí přírůstkově aktualizovat soubor s použitím pouze soubory .sbr, které se změnily.

BscMake – vyhledá, který má název zadaný pomocí možnosti /o soubor .bsc. Pokud není zadán /o, BSCMAKE hledá soubor, který má základní název prvního souboru .sbr a rozšíření .bsc. Pokud soubor existuje, BSCMAKE provádí přírůstkové sestavení z informačního souboru procházení pomocí přispívající soubory .sbr. Pokud soubor neexistuje, BSCMAKE provede úplné sestavení pomocí všechny soubory .sbr. Pravidla pro sestavení jsou následující:

- Pro úplné sestavení úspěšné všechny zadané soubory .sbr musí existovat a nesmí být zkrácena. Pokud soubor .sbr zkrácen, je nutné znovu sestavit ji (pomocí rekompilace nebo sestavení) před spuštěním nástroje BSCMAKE.

- Pro přírůstkové sestavení úspěšné musí existovat souboru .bsc. Všechny přispívající soubory .sbr i prázdné soubory, musí existovat a musí být zadán v příkazovém řádku nástroje BSCMAKE. Vynecháte-li soubor .sbr z příkazového řádku, BSCMAKE odebere jeho příspěvku ze souboru.

## <a name="see-also"></a>Viz také:

[Sestavení souboru .Bsc](../../build/reference/building-a-dot-bsc-file.md)
