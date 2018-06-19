---
title: C2026 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6b2952daa8cc7b3642cca5ba278990fde7d1ebe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167662"
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