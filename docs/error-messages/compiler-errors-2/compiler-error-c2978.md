---
title: "C2978 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2978
dev_langs: C++
helpviewer_keywords: C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3d02f0844cf3abe975531ec0560441c8eedd1ba6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2978"></a>C2978 chyby kompilátoru
Chyba syntaxe: byl očekáván 'keyword1' nebo 'keyword2'; byl nalezen typ 'keyword3'; parametry bez typu nejsou podporovány v obecných typech  
  
 Obecné třídy byla deklarována nesprávně. V tématu [obecné typy](../../windows/generics-cpp-component-extensions.md)Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2978.  
  
```  
// C2978.cpp  
// compile with: /clr /c  
generic <ref class T>   // C2978  
// try the following line instead  
// generic <typename T>   // OK  
ref class Utils {  
   static void sort(T elems, size_t size);  
};  
  
generic <int>  
// try the following line instead  
// generic <class T>  
ref class Utils2 {  
   static void sort(T elems, size_t size);  
};  
```