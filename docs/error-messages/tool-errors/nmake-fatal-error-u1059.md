---
title: Závažná chyba nástroje NMAKE U1059 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54919398c757bfe05f747ff57341f31decfc61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200787"
---
# <a name="nmake-fatal-error-u1059"></a>Závažná chyba nástroje NMAKE U1059

> Chyba syntaxe: "}" u závislé položky chybí

Cesty pro hledání adresu závislého byl nesprávně zadán. Buď místo existoval v cestě nebo pravou složenou závorku (**}**) byl vynechán.

Syntaxe specifikace adresáře pro závislé je

> **{** *adresáře* **} závislé**

kde *adresáře* Určuje jednu nebo více cest, každé oddělené středníkem (**;**). Nejsou povoleny mezery.

Pokud makro nahrazuje část nebo všechny cesty pro hledání, ujistěte se, že neexistují žádné mezery v rozšíření makra.