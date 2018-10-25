---
title: Chyba kompilátoru C2842 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6143249871384d89227d63fe1900814ae5077fd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055239"
---
# <a name="compiler-error-c2842"></a>Chyba kompilátoru C2842

'class': spravovaný typ WinRT nesmí definovat vlastní 'operator new' nebo 'operátor delete.

Můžete definovat vlastní ** operátor new nebo **operátor delete** Správa přidělování paměti na nativní haldě. Ale referenční třídy nelze definovat tyto operátory, protože jsou přiděleny pouze na spravované haldě.

Další informace najdete v tématu [uživatelem definované operátory (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2842.

```
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
