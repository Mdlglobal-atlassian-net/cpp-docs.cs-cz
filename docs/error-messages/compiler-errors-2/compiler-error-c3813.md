---
title: C3813 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e947b281c90c4d2ace83971f1de972c29bde72ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273104"
---
# <a name="compiler-error-c3813"></a>C3813 chyby kompilátoru
deklarace vlastnosti se může vyskytovat pouze v rámci definice spravované nebo WinRT typu  
  
A [vlastnost](../../dotnet/how-to-use-properties-in-cpp-cli.md) lze deklarovat pouze v rámci spravované nebo prostředí Windows Runtime typu. Nepodporuje nativní typy `property` – klíčové slovo.  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3813 a ukazuje, jak to opravit:  
  
```cpp  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```