---
title: Binární operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/14/2018
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
ms.openlocfilehash: 6c5ad5997657ce9f8a61383a2cd7e685f0a28751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036550"
---
# <a name="binary-operators"></a>Binární operátory

Následující tabulka uvádí seznam operátorů, které mohou být přetíženy.

## <a name="redefinable-binary-operators"></a>Binární operátory, které lze znovu definovat

|Operátor|Název|
|--------------|----------|
|**,**|Čárka|
|**\!=**|Nerovnost|
|**%**|Modulus|
|**%=**|Modulus/přiřazení|
|**&**|Bitový operátor AND|
|**&&**|Logický operátor AND|
|**&=**|Bitový operátor AND / přiřazení|
|**&#42;**|Násobení|
|**&#42;=**|Násobení/přiřazení|
|**+**|Sčítání|
|**+=**|Sčítání/přiřazení|
|**-**|Odčítání|
|**-=**|Odčítání/přiřazení|
|**->**|Výběr členů|
|**->&#42;**|Výběr pointer-to-member|
|**/**|Dělení|
|**/=**|Dělení/přiřazení|
|**<**|Menší než|
|**<<**|Posun doleva|
|**<<=**|Posunutí doleva / přiřazení|
|**<=**|Menší nebo rovno|
|**=**|Přiřazení|
|**==**|Rovnost|
|**>**|Větší než|
|**>=**|Větší nebo rovno|
|**>>**|Posun doprava|
|**>>=**|Posunutí doprava / přiřazení|
|**^**|Exkluzivní operátor OR|
|**^=**|Exkluzivní operátor OR / přiřazení|
|**&#124;**|Bitový inkluzivní operátor OR|
|**&#124;=**|Bitový operátor OR / přiřazení|
|**&#124;&#124;**|Logický operátor OR|

Chcete-li deklarovat funkci binárního operátoru jako nestatický člen, musíte ji deklarovat v podobě:

> *RET-type* **operátor** *op* **(** *arg* **)**

kde *ret-type* je návratový typ *op* je jedním z operátorů uvedených v předchozí tabulce a *arg* je argumentem libovolného typu.

Chcete-li deklarovat funkci binárního operátoru jako globální funkci, musíte ji deklarovat v podobě:

> *RET-type* **operátor** *op* **(** _arg1_**,** _arg2_ **)**

kde *ret-type* a *op* jsou popsány pro členské funkce operátora a *arg1* a *arg2* jsou argumenty. Alespoň jeden z argumentů musí být typu třídy.

> [!NOTE]
> Neexistuje žádné omezení na návratové typy binárních operátorů. Většina binárních operátorů definovaných uživatelem však vrátí typ třídy nebo odkaz na typ třídy.

## <a name="see-also"></a>Viz také:

[Přetížení operátoru](../cpp/operator-overloading.md)