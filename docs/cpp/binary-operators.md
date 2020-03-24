---
title: Binární operátory
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 030ae71fec7a0d1572804f30d09f6f9b2749e436
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181301"
---
# <a name="binary-operators"></a>Binární operátory

Následující tabulka uvádí seznam operátorů, které mohou být přetíženy.

## <a name="redefinable-binary-operators"></a>Binární operátory, které lze znovu definovat

|Operátor|Název|
|--------------|----------|
|**,**|Čárka|
|**!=**|Nerovnost|
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
|**->&#42;**|Výběr ukazatele na člena|
|**/**|Dělení|
|**/=**|Dělení/přiřazení|
|**<**|Je menší než|
|**<<**|Posun doleva|
|**<<=**|Posunutí doleva / přiřazení|
|**<=**|Je menší nebo rovno|
|**=**|Přiřazení|
|**==**|Rovnost|
|**>**|Větší než|
|**>=**|Je větší nebo rovno|
|**>>**|Posun doprava|
|**>>=**|Posunutí doprava / přiřazení|
|**^**|Exkluzivní nebo|
|**^=**|Exkluzivní operátor OR / přiřazení|
|**&#124;**|Bitový inkluzivní operátor OR|
|**&#124;=**|Bitový operátor OR / přiřazení|
|**&#124;&#124;**|Logický operátor OR|

Chcete-li deklarovat funkci binárního operátoru jako nestatický člen, musíte ji deklarovat v podobě:

> operátor *ret-Type* **operator** *op* **(** *arg* **)**

kde *ret-Type* je návratový typ, *op* je jedním z operátorů uvedených v předchozí tabulce a *arg* je argumentem libovolného typu.

Chcete-li deklarovat funkci binárního operátoru jako globální funkci, musíte ji deklarovat v podobě:

> operátor *ret-Type* **operator** *op* **(** _arg1_ **,** _arg2_ **)**

kde *ret-Type* a *op* jsou popsány pro funkce operátoru member a hodnota *arg1* a *arg2* jsou argumenty. Alespoň jeden z argumentů musí být typu třídy.

> [!NOTE]
> Neexistuje žádné omezení na návratové typy binárních operátorů. Většina binárních operátorů definovaných uživatelem však vrátí typ třídy nebo odkaz na typ třídy.

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
