---
title: Závažná chyba C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 6ed70a81c4ae2028d09b694f325f83454e99a587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203096"
---
# <a name="fatal-error-c1382"></a>Závažná chyba C1382

soubor PCH "File" byl znovu vytvořen, protože objekt obj byl vygenerován. Sestavte prosím tento objekt znovu.

Při použití [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)Kompilátor zjistil soubor. pch, který je novější než CIL. obj, který na něj odkazuje. Informace v souboru CIL. obj nejsou aktuální. Znovu Sestavte objekt.

C1382 může také nastat, pokud kompilujete pomocí **/YC**, ale také předat více souborů zdrojového kódu do kompilátoru.  Pro vyřešení Nepoužívejte **/YC** při předávání více souborů zdrojového kódu do kompilátoru.  Další informace naleznete v tématu [/Yc (Create a Compiled hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).
