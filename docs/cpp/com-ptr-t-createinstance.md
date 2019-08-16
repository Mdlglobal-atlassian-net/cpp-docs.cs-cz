---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 82b180b3f40683495ed2cfa284bdae8e1afaef9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498653"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Specifické pro společnost Microsoft**

Vytvoří novou instanci objektu daného typu `CLSID` nebo. `ProgID`

## <a name="syntax"></a>Syntaxe

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Parametry

*rclsid*<br/>
`CLSID` Objektu.

*clsidString*<br/>
Řetězec v kódování Unicode, který obsahuje `CLSID` znak (začínající znakem " **{** `ProgID`") nebo.

*clsidStringA*<br/>
Vícebajtový řetězec s použitím znakové stránky ANSI, který obsahuje buď `CLSID` (začínající znakem " **{** `ProgID`") nebo.

*dwClsContext*<br/>
Kontext spuštění spustitelného kódu.

*pOuter*<br/>
Vnější neznámý pro [agregaci](../atl/aggregation.md).

## <a name="remarks"></a>Poznámky

Tyto členské funkce volají `CoCreateInstance` k vytvoření nového objektu COM a dotazují se na typ rozhraní tohoto inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. `Release`je volána pro snížení počtu odkazů pro dříve zapouzdřený ukazatel. Tato rutina vrátí HRESULT, aby označovala úspěch nebo neúspěch.

- **CreateInstance (** *rclsid* **;** *dwClsContext* **)** Vytvoří novou spuštěnou instanci objektu s daným `CLSID`objektem.

- **CreateInstance (** *clsidString* **;** *dwClsContext* **)** Vytvoří novou spuštěnou instanci objektu podle řetězce Unicode, který obsahuje buď `CLSID` (začínající znakem " **{** `ProgID`") nebo.

- **CreateInstance (** *clsidStringA* **;** *dwClsContext* **)** Vytvoří novou spuštěnou instanci objektu předaným vícebajtovým znakovým řetězcem, který `CLSID` obsahuje buď (začínající znakem " **{** `ProgID`") nebo. Volá [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), která předpokládá, že řetězec je na znakové stránce ANSI, ne jako znaková stránka OEM.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)