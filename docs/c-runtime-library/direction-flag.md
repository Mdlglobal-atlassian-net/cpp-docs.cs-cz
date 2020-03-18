---
title: Příznak směru
ms.date: 11/04/2016
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: 04e096c6a62f806f4c214745a8401b1730eda3a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443390"
---
# <a name="direction-flag"></a>Příznak směru

Příznak směru je příznak procesoru specifický pro všechny procesory kompatibilní s platformou Intel x86. Vztahuje se na všechny pokyny k sestavení, které používají předponu (opakování), například MOVS, MOVSD, MOVSW a další. Adresy uvedené v příslušných pokynech se zvyšují, pokud je příznak směru vymazán.

Rutiny běhu jazyka C předpokládají, že příznak směru je vymazán. Pokud používáte jiné funkce s běhovými funkcemi jazyka C, je nutné zajistit, aby ostatní funkce ponechaly příznak Direction samostatně, nebo obnovit původní podmínku. Očekává se, že příznak směru, který má být jasný po vstupu, provede rychlejší a efektivnější kód za běhu.

Funkce běhové knihovny jazyka C, například rutiny pro manipulaci s řetězci a manipulaci s vyrovnávací pamětí, očekávají, že příznak směru bude jasný.

## <a name="see-also"></a>Viz také

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
