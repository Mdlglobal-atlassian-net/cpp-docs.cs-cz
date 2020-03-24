---
title: Závažná chyba C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: c349c09b4931c0a303e7619b364ab237394bd4fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204448"
---
# <a name="fatal-error-c1055"></a>Závažná chyba C1055

limit kompilátoru: došly klíče.

Zdrojový soubor obsahuje příliš mnoho symbolů. Kompilátor nemá klíče hash pro tabulku symbolů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Rozdělte zdrojový soubor na menší soubory.

1. Eliminujte nepotřebné hlavičkové soubory.

1. Místo vytváření nových proměnných znovu použijte dočasné a globální proměnné.
