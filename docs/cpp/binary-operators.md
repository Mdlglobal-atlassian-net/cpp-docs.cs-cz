---
title: "Binární operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a76b9505d11f17848232c69650c8e523bad91c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="binary-operators"></a>Binární operátory
Následující tabulka uvádí seznam operátorů, které mohou být přetíženy.  
  
### <a name="redefinable-binary-operators"></a>Binární operátory, které lze znovu definovat  
  
|Operátor|Název|  
|--------------|----------|  
|**,**|Čárka|  
|`!=`|Nerovnost|  
|`%`|Modulus|  
|`%=`|Modulus/přiřazení|  
|**&**|Bitový operátor AND|  
|**&&**|Logický operátor AND|  
|**&=**|Bitový operátor AND / přiřazení|  
|**\***|Násobení|  
|**\*=**|Násobení/přiřazení|  
|**+**|Sčítání|  
|`+=`|Sčítání/přiřazení|  
|**-**|Odčítání|  
|**-=**|Odčítání/přiřazení|  
|**->**|Výběr členů|  
|**->\***|Výběr ukazatele na člena|  
|**/**|Dělení|  
|`/=`|Dělení/přiřazení|  
|**<**|Menší než|  
|**<<**|Posun doleva|  
|**<<=**|Posunutí doleva / přiřazení|  
|**<=**|Menší nebo rovno|  
|**=**|Přiřazení|  
|`==`|Rovnost|  
|**>**|Větší než|  
|**>=**|Větší nebo rovno|  
|**>>**|Posun doprava|  
|**>>=**|Posunutí doprava / přiřazení|  
|**^**|Exkluzivní OR|  
|`^=`|Exkluzivní operátor OR / přiřazení|  
|**&#124;**|Bitový inkluzivní operátor OR|  
|`&#124;=`|Bitový operátor OR / přiřazení|  
|`&#124;&#124;`|Logický operátor OR|  
  
 Chcete-li deklarovat funkci binárního operátoru jako nestatický člen, musíte ji deklarovat v podobě:  
  
 *Vrácená hodnota typu* **operátor**`op`**(** `arg` **)**  
  
 kde *vrácená hodnota typu* je návratový typ `op` je jedním z operátory uvedené v předchozí tabulce, a `arg` je argument libovolného typu.  
  
 Chcete-li deklarovat funkci binárního operátoru jako globální funkci, musíte ji deklarovat v podobě:  
  
 *Vrácená hodnota typu* **operátor**`op`**(** `arg1` **,** `arg2` **)**  
  
 kde *vrácená hodnota typu* a `op` jsou popsané pro členské funkce operátor a `arg1` a `arg2` argumenty. Alespoň jeden z argumentů musí být typu třídy.  
  
> [!NOTE]
>  Neexistuje žádné omezení na návratové typy binárních operátorů. Většina binárních operátorů definovaných uživatelem však vrátí typ třídy nebo odkaz na typ třídy.  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)