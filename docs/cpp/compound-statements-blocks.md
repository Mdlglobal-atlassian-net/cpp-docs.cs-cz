---
title: Složené příkazy (bloky) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a8823935ee2f871cdc033aec23f05fc108244e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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