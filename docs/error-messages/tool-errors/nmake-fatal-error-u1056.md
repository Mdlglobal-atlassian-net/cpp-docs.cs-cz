---
title: Závažná chyba nástroje NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367262"
---
# <a name="nmake-fatal-error-u1056"></a>Závažná chyba nástroje NMAKE U1056

Nelze najít procesor příkazů.

Příkaz procesoru nebyla v cestě zadané v **COMSPEC** nebo **cesta** proměnné prostředí.

NMAKE používá COMMAND.COM nebo CMD. Soubor EXE jako příkazový procesor při provádění příkazů. Vyhledá procesor příkazu nejprve v cestě, nastavte **COMSPEC**. Pokud **COMSPEC** buď neexistuje, NMAKE prohledávání adresáře podle **cesta**.