---
title: Chyba kompilátoru C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651214"
---
# <a name="compiler-error-c3846"></a>Chyba kompilátoru C3846

'symbol': nejde naimportovat symbol z: 'assembly2': jako 'symbol' již byl importován z jiného sestavení "assembly1.

Symbol nejde importovat z odkazovaných sestavení, protože byly dříve importovány z odkazovaných sestavení.

## <a name="example"></a>Příklad

Následující ukázka generuje C3846:

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

A potom zkompilujete toto:

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
