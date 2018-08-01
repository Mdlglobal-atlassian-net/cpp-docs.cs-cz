---
title: přidělit | Dokumentace Microsoftu
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
ms.openlocfilehash: 82ce0af801b77a9566bd6395a9f03b05f41676d7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408518"
---
# <a name="allocate"></a>allocate
**Specifické pro Microsoft**  
  
 **Přidělit** Specifikátor deklarace pojmenuje datový segment, ve kterém bude datová položka přidělena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
   __declspec(allocate("segname")) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Název *segname* musí být deklarován pomocí jedné z následujících direktiv Pragma:  
  
-   [code_seg](../preprocessor/code-seg.md)  
  
-   [const_seg](../preprocessor/const-seg.md)  
  
-   [data_seg](../preprocessor/data-seg.md)  
  
-   [init_seg](../preprocessor/init-seg.md)  
  
-   [section](../preprocessor/section.md)  
  
## <a name="example"></a>Příklad  
  
```cpp 
// allocate.cpp  
#pragma section("mycode", read)  
__declspec(allocate("mycode"))  int i = 0;  
  
int main() {  
}  
```  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)