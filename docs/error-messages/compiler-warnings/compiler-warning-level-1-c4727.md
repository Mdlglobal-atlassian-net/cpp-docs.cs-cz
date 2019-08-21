---
title: Upozornění kompilátoru (úroveň 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 1bcc029536d2602d50178d7148332b8371db3c7f
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630835"
---
# <a name="compiler-warning-level-1-c4727"></a>Upozornění kompilátoru (úroveň 1) C4727

Soubor PCH s názvem pch_file se stejným časovým razítkem se našel v obj_file_1 a obj_file_2.  Použití prvního souboru PCH.

> [!NOTE]
> V aplikaci Visual Studio 2017 a starší je předkompilovaná hlavička ve výchozím nastavení označována jako *stdafx. h* a v aplikaci Visual Studio 2019 a novější je ve výchozím nastavení označována jako *PCH. h* .

K C4727 dochází při kompilování více compilands s **/YC**a tam, kde byl kompilátor schopný označit všechny soubory. obj stejným časovým razítkem. pch.

Chcete-li vyřešit, zkompilujte jeden zdrojový soubor pomocí **/YC/c** (vytvoří PCH) a ostatní se zkompiluje samostatně pomocí **/Yu/c** (používá PCH) a pak je propojí dohromady.

Takže pokud jste provedli následující a vygenerovali C4727:

::: moniker range="<=vs-2017"

**CL/CLR –/GL a. cpp b. cpp c. cpp/Ycstdafx.h**

Místo toho použijte následující:

**CL/CLR –/GL a. cpp/Ycstdafx.h/c**

**CL/CLR –/GL b. cpp c. cpp/Yustdafx.h/Link a. obj**

::: moniker-end

::: moniker range=">=vs-2019"

**CL/CLR –/GL a. cpp b. cpp c. cpp/Ycpch.h**

Místo toho použijte následující:

**CL/CLR –/GL a. cpp/Ycpch.h/c**

**CL/CLR –/GL b. cpp c. cpp/Yupch.h/Link a. obj**

::: moniker-end


Další informace naleznete v tématu

- [/Yc (vytvoření souboru předkompilované hlavičky)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (použití souboru předkompilované hlavičky)](../../build/reference/yu-use-precompiled-header-file.md)