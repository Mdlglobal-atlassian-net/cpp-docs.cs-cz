---
title: Závažná chyba nástroje NMAKE U1095
ms.date: 11/04/2016
f1_keywords:
- U1095
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
ms.openlocfilehash: 55c7ca7d237655b7e20406e7f28e5b2471bdec53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193456"
---
# <a name="nmake-fatal-error-u1095"></a>Závažná chyba nástroje NMAKE U1095

příkazový řádek příkazu CommandLine byl příliš dlouhý.

Po rozšíření makra překročil zadaný příkazový řádek limit délky příkazových řádků pro operační systém.

Systém MS-DOS povoluje až 128 znaků v příkazovém řádku.

Pokud je příkaz pro program, který může přijmout vstup z příkazového řádku ze souboru, změňte příkaz a zadejte vstup z souboru na disk nebo do vloženého souboru. Například odkaz a LIB akceptuje vstup ze souboru odpovědí.
