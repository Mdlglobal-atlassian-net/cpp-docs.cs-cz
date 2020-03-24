---
title: Chyba kompilátoru C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177453"
---
# <a name="compiler-error-c2567"></a>Chyba kompilátoru C2567

nejde otevřít metadata v souboru File, soubor je možná odstraněný nebo přesunutý.

Soubor metadat, na který byl odkazován ve zdroji (s `#using`), nebyl nalezen ve stejném adresáři jako proces back-endu kompilátoru, protože byl procesem front-end kompilátoru. Další informace najdete v tématu [direktiva #using](../../preprocessor/hash-using-directive-cpp.md) .

C2567 může být způsobena tím, že kompilujete pomocí **/c** na jednom počítači a pak pokusíte vytvořit kód při propojování v jiném počítači. Další informace naleznete v tématu [/LTCG (generování kódu při propojování)](../../build/reference/ltcg-link-time-code-generation.md)).

Může to také znamenat, že váš počítač neměl k dispozici více paměti.

Chcete-li opravit tuto chybu, zajistěte, aby byl soubor metadat ve stejném adresáři pro všechny fáze procesu sestavení.
