---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187528"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Specifické pro společnost Microsoft**

Vytvoří objekt `_variant_t`.

## <a name="syntax"></a>Syntaxe

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
Objekt `VARIANT`, který se má zkopírovat do nového objektu `_variant_t`.

*pVarSrc*<br/>
Ukazatel na objekt `VARIANT`, který se má zkopírovat do nového objektu `_variant_t`

*var_t_Src*<br/>
Objekt `_variant_t`, který se má zkopírovat do nového objektu `_variant_t`.

*fCopy*<br/>
V případě **hodnoty false**je zadaný objekt `VARIANT` připojen k novému objektu `_variant_t`, aniž by bylo nutné vytvořit novou kopii pomocí `VariantCopy`.

*ISrc, sSrc*<br/>
Celočíselná hodnota, která se má zkopírovat do nového objektu `_variant_t`.

*vtSrc*<br/>
`VARTYPE` pro nový objekt `_variant_t`

*fltSrc, dblSrc*<br/>
Číselná hodnota, která se má zkopírovat do nového objektu `_variant_t`.

*cySrc*<br/>
Objekt `CY`, který se má zkopírovat do nového objektu `_variant_t`.

*bstrSrc*<br/>
Objekt `_bstr_t`, který se má zkopírovat do nového objektu `_variant_t`.

*strSrc, wstrSrc*<br/>
Řetězec, který má být zkopírován do nového objektu `_variant_t`.

*bSrc*<br/>
**Logická** hodnota, která se má zkopírovat do nového objektu `_variant_t`.

*pIUknownSrc*<br/>
Rozhraní modelu COM ukazatel na objekt VT_UNKNOWN, který se má zapouzdřit do nového objektu `_variant_t`.

*pDispSrc*<br/>
Rozhraní modelu COM ukazatel na objekt VT_DISPATCH, který se má zapouzdřit do nového objektu `_variant_t`.

*decSrc*<br/>
Hodnota `DECIMAL`, která se má zkopírovat do nového objektu `_variant_t`

*bSrc*<br/>
Hodnota `BYTE`, která se má zkopírovat do nového objektu `_variant_t`

*cSrc*<br/>
Hodnota typu **char** , která se má zkopírovat do nového objektu `_variant_t`.

*usSrc*<br/>
**Krátká hodnota bez znaménka** , která se má zkopírovat do nového objektu `_variant_t`.

*ulSrc*<br/>
Hodnota **Long bez znaménka** k zkopírování do nového objektu `_variant_t`.

*iSrc*<br/>
Hodnota typu **int** , která se má zkopírovat do nového objektu `_variant_t`

*uiSrc*<br/>
Do nového objektu `_variant_t` se zkopírují **nepodepsaná hodnota int** , která se má zkopírovat.

*i8Src*<br/>
Hodnota **__int64** , která se má zkopírovat do nového objektu `_variant_t`

*ui8Src*<br/>
Hodnota **bez znaménka __int64** , která se má zkopírovat do nového objektu `_variant_t`

## <a name="remarks"></a>Poznámky

- **_variant_t ()** Vytvoří prázdný objekt `_variant_t` `VT_EMPTY`.

- **_variant_t (variant &**  *varSrc*  **)** Vytvoří objekt `_variant_t` z kopie objektu `VARIANT`. Typ variant je zachován.

- **_variant_t (variant** <strong>\*</strong> *pVarSrc* **)** Vytvoří objekt `_variant_t` z kopie objektu `VARIANT`. Typ variant je zachován.

- **_variant_t (_variant_t &**  *var_t_Src*  **)** Vytvoří objekt `_variant_t` z jiného objektu `_variant_t`. Typ variant je zachován.

- **_variant_t (variant &** *varSrc* **, bool**`fCopy` **)** Vytvoří objekt `_variant_t` z existujícího objektu `VARIANT`. Pokud *fCopy* je fCopy **false**, objekt **variant** je připojen k novému objektu bez vytvoření kopie.

- **_variant_t (Short***sSrc* **, VARTYPE**`vtSrc` **= VT_I2)** Vytvoří objekt `_variant_t` typu VT_I2 nebo VT_BOOL z **krátkých** celočíselných hodnot. Všechny ostatní `VARTYPE` mají za následek chybu E_INVALIDARG.

- **_variant_t (long**`lSrc` **, VARTYPE**`vtSrc` **= VT_I4)** Vytvoří objekt `_variant_t` typu VT_I4, VT_BOOL nebo VT_ERROR z **dlouhé** celočíselné hodnoty. Všechny ostatní `VARTYPE` mají za následek chybu E_INVALIDARG.

- **_variant_t (float**`fltSrc` **)** Vytvoří objekt `_variant_t` typu VT_R4 z číselné hodnoty typu **float** .

- **_variant_t (double**`dblSrc` **, VARTYPE**`vtSrc` **= VT_R8)** Vytvoří objekt `_variant_t` typu VT_R8 nebo VT_DATE z **dvojité** číselné hodnoty. Všechny ostatní `VARTYPE` mají za následek chybu E_INVALIDARG.

- **_variant_t (CY &** `cySrc` **)** Vytvoří objekt `_variant_t` typu VT_CY z objektu `CY`.

- **_variant_t (_bstr_t &** `bstrSrc` **)** Vytvoří objekt `_variant_t` typu VT_BSTR z objektu `_bstr_t`. Je přidělen nový `BSTR`.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** Vytvoří objekt `_variant_t` typu VT_BSTR z řetězce Unicode. Je přidělen nový `BSTR`.

- **_variant_t (char** <strong>\*</strong>`strSrc` **)** Vytvoří objekt `_variant_t` typu VT_BSTR z řetězce. Je přidělen nový `BSTR`.

- **_variant_t (bool**`bSrc` **)** Vytvoří objekt `_variant_t` typu VT_BOOL z **logické** hodnoty.

- **_variant_t (IUnknown** <strong>\*</strong>`pIUknownSrc` **, bool**`fAddRef` **= true)** Vytvoří objekt `_variant_t` typu VT_UNKNOWN z ukazatele rozhraní modelu COM. Pokud `fAddRef` má **hodnotu true**, pak je `AddRef` volána v zadaném ukazateli rozhraní tak, aby odpovídala volání `Release`, ke kterému dojde, když je objekt `_variant_t` zničen. Je až do volání `Release` na zadaném ukazateli rozhraní. Pokud je `fAddRef` **false**, převezme tento konstruktor vlastnictví zadaného ukazatele rozhraní; Nevolejte `Release` na zadaný ukazatel rozhraní.

- **_variant_t (IDispatch** <strong>\*</strong>`pDispSrc` **, bool**`fAddRef` **= true)** Vytvoří objekt `_variant_t` typu VT_DISPATCH z ukazatele rozhraní modelu COM. Pokud `fAddRef` má **hodnotu true**, pak je `AddRef` volána v zadaném ukazateli rozhraní tak, aby odpovídala volání `Release`, ke kterému dojde, když je objekt `_variant_t` zničen. Je až do volání `Release` na zadaném ukazateli rozhraní. Pokud je `fAddRef` **false**, převezme tento konstruktor vlastnictví zadaného ukazatele rozhraní; Nevolejte `Release` na zadaný ukazatel rozhraní.

- **_variant_t (desítkové &** `decSrc` **)** Vytvoří objekt `_variant_t` typu VT_DECIMAL z `DECIMAL` hodnoty.

- **_variant_t (BYTE**`bSrc` **)** Vytvoří objekt `_variant_t` typu `VT_UI1` z `BYTE` hodnoty.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_variant_t – třída](../cpp/variant-t-class.md)
