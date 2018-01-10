---
title: "Složené příkazy (bloky) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs: C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36dc3c25d5f8bbd37ebfaa3458c07f6948492817
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compound-statements-blocks"></a>Složené příkazy (bloky)
Složený příkaz se skládá z počtu nula či více příkazy ve složené závorce (**{}**). Složený příkaz lze použít všude, kde je očekáván příkaz. Složené příkazy jsou často označovány za „bloky“.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
{ [ statement-list ] }  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující příklad používá složený příkaz jako *příkaz* součástí **Pokud** – příkaz (najdete v části [zda příkaz](../cpp/if-else-statement-cpp.md) podrobnosti o syntaxi):  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
{
    Balance -= Amount;  
}
```  
  
> [!NOTE]
>  Protože deklaraci je prohlášení, deklaraci může být jedna z příkazy v *seznam příkazů*. Důsledkem toho mají názvy deklarované uvnitř složeného příkazu (ale nikoli explicitně deklarované jako statické) místní obor a v případě objektů i životnost. V tématu [oboru](../cpp/scope-visual-cpp.md) podrobnosti o zacházení s místní obor názvů.  
  
## <a name="see-also"></a>Viz také  
 [Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)