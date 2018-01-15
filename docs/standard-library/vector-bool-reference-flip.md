---
title: "vektor&lt;bool&gt;:: Reference::Flip – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vector/std::vector<bool>::reference::flip
dev_langs: C++
helpviewer_keywords: reference::flip method
ms.assetid: ef940365-cbe4-4a87-a3e2-1f3cfa357e29
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 87ff43b6164ce12dc71334c6cc6f8f8728776e27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vectorltboolgtreferenceflip"></a>vektor&lt;bool&gt;:: Reference::Flip –
Invertuje výběr logická hodnota odkazovaný [vektoru\<bool >](../standard-library/vector-bool-class.md) element.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void flip();
```  
  
## <a name="example"></a>Příklad  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
## <a name="output"></a>Výstup  
  
```  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<vektoru >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [vektor\<bool >:: odkazovat – třída](../standard-library/vector-bool-reference-class.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)

