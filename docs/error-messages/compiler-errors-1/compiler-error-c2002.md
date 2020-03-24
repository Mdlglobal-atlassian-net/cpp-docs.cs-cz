---
title: Chyba kompilátoru C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208244"
---
# <a name="compiler-error-c2002"></a>Chyba kompilátoru C2002

Neplatná konstanta s velkým znakem

Konstanta vícebajtových znaků není platná.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Konstanta s velkým znakem obsahuje více bajtů, než se očekávalo.

1. Standardní hlavička STDDEF. h není zahrnutá.

1. Pro velké znaky nelze zřetězit pomocí běžných řetězcových literálů.

1. Konstanta s velkým znakem musí předcházet znak L:

    ```
    L'mbconst'
    ```

1. V případě C++Microsoft musí být textové argumenty direktivy preprocesoru znakové sady ASCII. Například Direktiva `#pragma message(L"string")`není platná.
