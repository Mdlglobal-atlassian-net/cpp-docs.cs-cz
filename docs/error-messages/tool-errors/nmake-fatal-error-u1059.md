---
title: Závažná chyba nástroje NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182835"
---
# <a name="nmake-fatal-error-u1059"></a>Závažná chyba nástroje NMAKE U1059

> Chyba syntaxe: v závislosti chybí znak}.

Nebyla správně zadána cesta pro hledání závislé položky. Buď existovalo místo v cestě, nebo pravá složená závorka ( **}** ) byla vynechána.

Syntaxe specifikace adresáře pro závislý je

> závislé na **{** *directories* Directory **}**

kde *adresářs* Určuje jednu nebo více cest, z nichž každá je oddělena středníkem ( **;** ). Nejsou povoleny žádné mezery.

Pokud je část nebo celá cesta pro hledání nahrazena makrem, ujistěte se, že v rozšíření makra neexistují žádné mezery.
