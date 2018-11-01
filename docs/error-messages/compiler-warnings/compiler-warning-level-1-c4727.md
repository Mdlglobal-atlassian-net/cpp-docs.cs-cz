---
title: Kompilátor upozornění (úroveň 1) C4727
ms.date: 11/04/2016
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: be1a248fc2709706e137b543344966735c19064e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490568"
---
# <a name="compiler-warning-level-1-c4727"></a>Kompilátor upozornění (úroveň 1) C4727

"S názvem pch_file se stejným časovým razítkem se našel v obj_file_1 a obj_file_2 PCH.  Pomocí první soubor PCH.

C4727 nastane při kompilaci několika souborech určených ke kompilaci s **/Yc**, a pokud bylo možné označit všechny soubory .obj se stejným časovým razítkem .pch kompilátor.

Pokud chcete vyřešit, kompilaci jednoho zdrojového souboru s **/Yc /c** (vytvoří pch), a ostatní samostatně zkompilovat s **/Yu /c** (používá pch), poté je propojit dohromady.

Takže pokud jste následující a generuje C4727:

**cl/CLR/GL. a.cpp b.cpp c.cpp /Ycstdafx.h**

Můžete by postupujte takto:

**cl/CLR/GL. a.cpp /Ycstdafx.h /c**

**/ Link a.obj /Yustdafx.h b.cpp c.cpp cl/CLR/GL.**

Další informace naleznete v tématu

- [/Yc (vytvoření souboru předkompilované hlavičky)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (použití souboru předkompilované hlavičky)](../../build/reference/yu-use-precompiled-header-file.md)