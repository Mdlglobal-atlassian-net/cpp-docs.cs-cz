---
title: Chyba nástroje BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197636"
---
# <a name="bscmake-error-bk1513"></a>Chyba nástroje BSCMAKE BK1513

Nepřírůstková aktualizace vyžaduje vše. Soubory SBR

BSCMAKE nemůže vytvořit nový soubor s informacemi o procházení (. BSC), protože jeden nebo více souborů. SBR je zkráceno. Pokud chcete najít názvy zkrácených souborů. SBR, přečtěte si upozornění [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) , která doprovázejí tuto chybu.

BSCMAKE může aktualizovat soubor. BSC se zkráceným souborem. SBR, ale nemůže vytvořit nový. BSCMAKE může vytvořit nový soubor. BSC z následujících důvodů:

- Chybí soubor. BSC.

- Pro soubor. BSC byl zadán nesprávný název souboru.

- Soubor. BSC je poškozen.

Chcete-li tento problém vyřešit, odstraňte zkrácené soubory. sbr a znovu sestavte nebo vyčistěte řešení a znovu sestavte. (V integrovaném vývojovém prostředí zvolte **sestavit**, **Vyčistit řešení**a pak zvolte **sestavit**, znovu **Sestavit řešení**.)
