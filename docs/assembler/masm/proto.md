---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 24ec2a9abc6c8b76fc81f6d412019296c53160f4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74394759"
---
# <a name="proto"></a>PROTO

Vytvoří prototypy funkce nebo procedury. Můžete zavolat funkci, kterou prototypuje, pomocí direktivy [Invoke](invoke.md) .

## <a name="syntax"></a>Syntaxe

> *Label* **proto** ⟦*Distance*⟧ ⟦*Language-Type*⟧ ⟦ __,__ ⟦*parametr*⟧ __:__ *tag* ... ⟧

### <a name="parameters"></a>Parametry

\ *popisku*
Název prototypované funkce.

\ *vzdálenosti*
Volitelné Používá se v 16bitových modelech paměti k přepsání výchozí hodnoty a označení **blízko** nebo **daleko** volání.

\ *typu jazyka*
Volitelné Nastaví konvenci volání a pojmenování pro procedury a veřejné symboly. Podporované konvence:

- 32 bitová **plochý** model: **C**, **STDCALL**

- 16bitové modely: **C**, **Basic**, **FORTRAN**, **Pascal**, **syscall**, **STDCALL**

\ *parametru*
Volitelný název parametru funkce.

\ *značek*
Typ parametru funkce.

Parametry *parametrů* a *značek* se mohou u každého předaného argumentu zobrazit víckrát.

## <a name="example"></a>Příklad

Tato ukázka **ukazuje deklaraci** pro funkci s názvem `addup3`, která používá volání **poblíž** pro přepsání 16bitového modelu výchozí pro volání procedur a používá konvenci volání **jazyka C** pro parametry zásobníku a návratové hodnoty. Přebírá dva argumenty, **slovo** a **vararg**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[. Odkaz na MODEL](dot-model.md)
