---
title: přidělit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- allocate_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0a253d1b539d1f3d2648cba5fa41b6d1cfbc955
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="allocate"></a>allocate
**Konkrétní Microsoft**  
  
 **Přidělit** deklarace specifikátor názvy datového segmentu, ve kterém se přidělí datová položka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  

   __declspec(allocate("segname")) declarator  

```  
  
## <a name="remarks"></a>Poznámky  
 Název *segname* musí být deklarován pomocí jedné z následujících direktivy:  
  
-   [code_seg](../preprocessor/code-seg.md)  
  
-   [const_seg](../preprocessor/const-seg.md)  
  
-   [data_seg](../preprocessor/data-seg.md)  
  
-   [init_seg](../preprocessor/init-seg.md)  
  
-   [section](../preprocessor/section.md)  
  
## <a name="example"></a>Příklad  
  
```  
// allocate.cpp  
#pragma section("mycode", read)  
__declspec(allocate("mycode"))  int i = 0;  
  
int main() {  
}  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)