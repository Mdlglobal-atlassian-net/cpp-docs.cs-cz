---
title: Binární operátory
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 700d8fd784862c3e9f81fcde839063ff0a4696bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602403"
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