---
title: PROTO
ms.date: 12/06/2019
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 9df66b6c89498a2cc1a1864a668b7addfbaf593c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987867"
---
# <a name="proto"></a>PROTO

Vytvoří prototypy funkce nebo procedury. Můžete zavolat funkci, kterou prototypuje, pomocí direktivy [Invoke](invoke.md) .

## <a name="syntax"></a>Syntaxe

> *Label* **proto** ⟦*Distance*⟧ ⟦*Language-Type*⟧ ⟦ __,__ ⟦*parametr*⟧ __:__ *tag* ... ⟧

### <a name="parameters"></a>Parametry

\ *popisku*
Název prototypované funkce.

*Distance* (jenom 32-bit MASM) \
Volitelné Používá se v 16bitových modelech paměti k přepsání výchozí hodnoty a označení **blízko** nebo **daleko** volání.

*typ jazyka* (jenom 32-bit MASM) \
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
