---
title: Závažná chyba nástroje NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182900"
---
# <a name="nmake-fatal-error-u1056"></a>Závažná chyba nástroje NMAKE U1056

Nejde najít procesor příkazů.

Procesor příkazů nebyl v cestě zadané v proměnných prostředí **ComSpec** nebo **path** .

Nástroj NMAKE používá COMMAND.COM nebo CMD. EXE jako příkazový procesor při provádění příkazů. Vyhledá jako první příkazový procesor v cestě nastavené v **ComSpec**. Pokud **ComSpec** neexistuje, NMAKE vyhledá adresáře zadané v **cestě**.
