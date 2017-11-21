---
title: "C2026 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2026
dev_langs: C++
helpviewer_keywords: C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 97937579c12730fecfa89c69d9e7cf51229b5c6c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2026"></a>C2026 chyby kompilátoru
řetězec je příliš velký, koncové znaky zkrácen.  
  
 Řetězec byl delší než limit 16380 jednobajtové znaky.  
  
 Před přiléhající řetězce se zřetězených řetězec nesmí být delší než 16380 jednobajtové znaky.  
  
 Řetězec znaků Unicode o polovinu této délky by také vygeneroval tuto chybu.  
  
 Pokud máte definovány takto řetězec, generuje C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 Vám může jej rozdělte následujícím způsobem:  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 Můžete k uložení mimořádně velký textové literály (32 kB nebo více) ve vlastní prostředek nebo externí soubor. V tématu [vytvoření nového vlastního prostředku nebo prostředku dat](../../windows/creating-a-new-custom-or-data-resource.md) Další informace.