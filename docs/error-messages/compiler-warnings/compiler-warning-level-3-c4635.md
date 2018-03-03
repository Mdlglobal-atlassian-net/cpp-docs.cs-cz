---
title: "Kompilátoru (úroveň 3) upozornění C4635 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16b6a19618afeed952cfa594961a0e4ccb777d26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4635"></a>C4635 kompilátoru upozornění (úroveň 3)
Cíl komentář dokumentu XML: chybně formátovanou XML: důvod  
  
 Kompilátor najít nějaký problém s značky XML.  Opravte problém a pak ji znovu zkompilovat  
  
 Následující ukázka generuje C4635:  
  
```  
// C4635.cpp  
// compile with: /doc /clr /W3 /c  
/// <summary>     
/// The contents of the folder have changed.  
/// <summary/>   // C4635  
  
// try the following line instead  
// /// </summary>  
public ref class Test {};  
```  
  
 Všimněte si, že výstup pro tato ukázka uvádí: **"člen" koncová značka neodpovídá počáteční značce 'souhrn'.**  
  
 Problém s Tato ukázka je, že koncová značka pro \<souhrnné > má chybný formát a kompilátor nerozpoznává jej jako \<souhrnné > ukončovací značku.  \<Člen > značky vložené v souboru projektový kompilátorem v každé/doc kompilaci.  Ano, problémem je, že koncová značka \</member >, neodpovídá předchozí počáteční značky, který zpracovává kompilátor (\<souhrnné >.