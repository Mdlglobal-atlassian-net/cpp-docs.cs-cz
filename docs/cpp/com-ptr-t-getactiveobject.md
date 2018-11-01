---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: 84e43de9c40baa3c596c68ed7739471c059cbac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484497"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Specifické pro Microsoft**

Připojí se k existující instanci objektu dle `CLSID` nebo `ProgID`.

## <a name="syntax"></a>Syntaxe

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>Parametry

*rclsid*<br/>
`CLSID` Objektu.

*clsidString*<br/>
Řetězec znaků Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.

*clsidStringA*<br/>
Vícebajtový řetězec používající znakovou stránku ANSI, který udržuje `CLSID` (počínaje "**{**") nebo `ProgID`.

## <a name="remarks"></a>Poznámky

Tyto členské funkce volají **GetActiveObject** níž načítají ukazatel na spuštěný objekt registrovaný technologií OLE a potom dotazy pro tohoto inteligentního ukazatele typu rozhraní. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel. Tato rutina vrátí hodnotu HRESULT indikuje úspěch nebo selhání.

- **GetActiveObject (**`rclsid`**)** připojí k existující instanci objektu dle `CLSID`.

- **GetActiveObject (**`clsidString`**)** připojí k existující instanci objektu dle řetězce Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.

- **GetActiveObject (**`clsidStringA`**)** připojí k existující instanci objektu dle vícebajtového řetězce znaků obsahujícího `CLSID` (počínaje "**{**") nebo `ProgID`. Volání [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), kde se předpokládá, že je řetězec uložen ve znakovou stránku ANSI, nikoli znakovou stránku OEM.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)