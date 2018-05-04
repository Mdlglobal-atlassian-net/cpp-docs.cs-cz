---
title: Binární operátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b930c548ea411beb03255d694f2423903053288
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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