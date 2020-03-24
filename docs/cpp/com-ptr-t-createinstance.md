---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 2ec4e90c8f0c1009cc47e9022a09b3b8f7dbb284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189998"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Specifické pro společnost Microsoft**

Vytvoří novou instanci objektu daného `CLSID` nebo `ProgID`.

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
`CLSID` objektu.

*clsidString*<br/>
Řetězec v kódování Unicode, který obsahuje `CLSID` (začínající znakem " **{** ") nebo `ProgID`.

*clsidStringA*<br/>
Vícebajtový řetězec s použitím znakové stránky ANSI, který obsahuje buď `CLSID` (začínající znakem " **{** ") nebo `ProgID`.

*dwClsContext*<br/>
Kontext spuštění spustitelného kódu.

*pOuter*<br/>
Vnější neznámý pro [agregaci](../atl/aggregation.md).

## <a name="remarks"></a>Poznámky

Tyto členské funkce volají `CoCreateInstance` pro vytvoření nového objektu COM a dotazování pro typ rozhraní inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. je volána `Release` pro snížení počtu odkazů pro dříve zapouzdřený ukazatel. Tato rutina vrátí HRESULT, aby označovala úspěch nebo neúspěch.

- **CreateInstance (**  *rclsid* **;**  *dwClsContext*  **)** Vytvoří novou spuštěnou instanci objektu s daným `CLSID`.

- **CreateInstance (**  *clsidString* **;**  *dwClsContext*  **)** Vytvoří novou spuštěnou instanci objektu podle řetězce Unicode, který obsahuje buď `CLSID` (začínající znakem " **{** ") nebo `ProgID`.

- **CreateInstance (**  *clsidStringA* **;**  *dwClsContext*  **)** Vytvoří novou spuštěnou instanci objektu s předaným vícebajtovým znakovým řetězcem, který obsahuje buď `CLSID` (začínající znakem " **{** ") nebo `ProgID`. Volá [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), která předpokládá, že řetězec je na znakové stránce ANSI, ne jako znaková stránka OEM.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
