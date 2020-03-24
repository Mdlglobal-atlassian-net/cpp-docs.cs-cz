---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 402251592a87b723d75fd1b2cd0786be7b17dbfc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187619"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Specifické pro společnost Microsoft**

## <a name="syntax"></a>Syntaxe

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>Poznámky

Operátor přiřadí novou hodnotu objektu `_variant_t`:

- **operator = (**  *varSrc*  **)** – operátor Přiřadí existující `VARIANT` k objektu `_variant_t`.

- **operator = (**  *pVarSrc*  **)** – operátor Přiřadí existující `VARIANT` k objektu `_variant_t`.

- **operator = (**  *var_t_Src*  **)** – operátor Přiřadí existující objekt `_variant_t` k objektu `_variant_t`.

- **operator = (** *sSrc* **)** – operátor Přiřadí k objektu `_variant_t` **krátkou** celočíselnou hodnotu.

- **operator = (** `lSrc` **)** – operátor Přiřadí celočíselnou hodnotu typu **Long** k objektu `_variant_t`.

- **operator = (**  *fltSrc*  **)** – operátor Přiřadí číselnou hodnotu **typu float** objektu `_variant_t`.

- **operator = (** *dblSrc* **)** – operátor Přiřadí hodnotu typu `_variant_t` k objektu, který je **dvojnásobnou** číselnou hodnotou.

- **operator = (**  *cySrc*  **)** – operátor Přiřadí objekt `CY` k objektu `_variant_t`.

- **operator = (**  *bstrSrc*  **)** – operátor Přiřadí objekt `BSTR` k objektu `_variant_t`.

- **operator = (**  *wstrSrc*  **)** – operátor Přiřadí řetězec v kódování Unicode k objektu `_variant_t`.

- **operator = (** `strSrc` **)** – operátor Přiřadí vícebajtový řetězec k objektu `_variant_t`.

- **operator = (** `bSrc` **)** – operátor Přiřadí hodnotu **bool** objektu `_variant_t`.

- **operator = (**  *pDispSrc*  **)** – operátor Přiřadí objekt `VT_DISPATCH` k objektu `_variant_t`.

- **operator = (**  *pIUnknownSrc*  **)** – operátor Přiřadí objekt `VT_UNKNOWN` k objektu `_variant_t`.

- **operator = (**  *decSrc*  **)** – operátor Přiřadí hodnotu `DECIMAL` objektu `_variant_t`.

- **operator = (** `bSrc` **)** – operátor Přiřadí hodnotu `BYTE` objektu `_variant_t`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
