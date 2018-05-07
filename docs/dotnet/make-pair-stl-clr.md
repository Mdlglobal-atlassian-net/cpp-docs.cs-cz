---
title: make_pair – (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::make_pair
dev_langs:
- C++
helpviewer_keywords:
- make_pair function [STL/CLR]
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99e2cc7bc7255940b28f2f85dae1a7cbebd6df46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="makepair-stlclr"></a>make_pair (STL/CLR)
Ujistěte se, `pair` z dvojici hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Value1`  
 Typ první zabalená hodnota.  
  
 `Value2`  
 Typ druhého zabalená hodnota.  
  
 `first`  
 První hodnota zabalit.  
  
 `second`  
 Druhá hodnota zabalit.  
  
## <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí `pair<Value1, Value2>(first, second)`. Lze použít k sestavení `pair<Value1, Value2>` objekt z dvojici hodnot.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / nástroj >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)