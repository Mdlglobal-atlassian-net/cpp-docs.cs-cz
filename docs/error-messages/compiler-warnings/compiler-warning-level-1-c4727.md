---
title: Upozornění kompilátoru (úroveň 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 0c00ac552e525fd57f6f09b0be5655958cfce3cc
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075143"
---
# <a name="compiler-warning-level-1-c4727"></a>Upozornění kompilátoru (úroveň 1) C4727

V obj_file_1 a obj_file_2 byl nalezen "PCH s názvem pch_file se stejným časovým razítkem.  Použití prvního souboru PCH.

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

Další informace najdete v tématu

- [/Yc (vytvoření souboru předkompilované hlavičky)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (použití souboru předkompilované hlavičky)](../../build/reference/yu-use-precompiled-header-file.md)