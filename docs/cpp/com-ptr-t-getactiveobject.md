---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170798"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Specifické pro společnost Microsoft**

Připojí se k existující instanci objektu daného `CLSID` nebo `ProgID`.

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
`CLSID` objektu.

*clsidString*<br/>
Řetězec v kódování Unicode, který obsahuje `CLSID` (začínající znakem " **{** ") nebo `ProgID`.

*clsidStringA*<br/>
Vícebajtový řetězec s použitím znakové stránky ANSI, který obsahuje buď `CLSID` (začínající znakem " **{** ") nebo `ProgID`.

## <a name="remarks"></a>Poznámky

Tyto členské funkce volají **GetActiveObject** , aby načetly ukazatel na běžící objekt, který byl zaregistrován pomocí technologie OLE a následně zadá dotazy pro typ rozhraní inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. je volána `Release` pro snížení počtu odkazů pro dříve zapouzdřený ukazatel. Tato rutina vrátí HRESULT, aby označovala úspěch nebo neúspěch.

- **GetActiveObject (** `rclsid` **)** Připojí se k existující instanci objektu daného `CLSID`.

- **GetActiveObject (** `clsidString` **)** Připojí se k existující instanci objektu dle řetězce Unicode, který obsahuje `CLSID` (začínající znakem " **{** ") nebo `ProgID`.

- **GetActiveObject (** `clsidStringA` **)** Připojí se k existující instanci objektu předaným vícebajtovým znakovým řetězcem, který obsahuje buď `CLSID` (začínající znakem " **{** ") nebo `ProgID`. Volá [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), která předpokládá, že řetězec je na znakové stránce ANSI, ne jako znaková stránka OEM.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
