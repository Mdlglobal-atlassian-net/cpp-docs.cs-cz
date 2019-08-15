---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498896"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Specifické pro společnost Microsoft**

Připojí se k existující instanci objektu daného typu `CLSID` nebo. `ProgID`

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
Řetězec v kódování Unicode, který obsahuje `CLSID` znak (začínající znakem " **{** `ProgID`") nebo.

*clsidStringA*<br/>
Vícebajtový řetězec s použitím znakové stránky ANSI, který obsahuje buď `CLSID` (začínající znakem " **{** `ProgID`") nebo.

## <a name="remarks"></a>Poznámky

Tyto členské funkce volají **GetActiveObject** , aby načetly ukazatel na běžící objekt, který byl zaregistrován pomocí technologie OLE a následně zadá dotazy pro typ rozhraní inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. `Release`je volána pro snížení počtu odkazů pro dříve zapouzdřený ukazatel. Tato rutina vrátí HRESULT, aby označovala úspěch nebo neúspěch.

- **GetActiveObject (** `rclsid` **)** připojí se k existující instanci objektu daného typu `CLSID`.

- **GetActiveObject (** `clsidString` **)** připojí se k existující instanci objektu dle `CLSID` řetězce Unicode, který obsahuje buď ( `ProgID`začínající znakem " **{** ") nebo.

- **GetActiveObject (** `clsidStringA` **)** připojí se k existující instanci objektu předaným vícebajtovým znakovým `CLSID` řetězcem, který obsahuje buď ( `ProgID`začínající znakem " **{** ") nebo. Volá [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), která předpokládá, že řetězec je na znakové stránce ANSI, ne jako znaková stránka OEM.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)