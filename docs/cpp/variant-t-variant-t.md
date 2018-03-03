---
title: _variant_t::_variant_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd85a54e9f73352894f6575051fe1ea8be0698fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
**Konkrétní Microsoft**  
  
 Vytvoří `_variant_t` objektu.  
  
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
 *varSrc*  
 A **VARIANT** objekt, který má být zkopírován do nové `_variant_t` objektu.  
  
 *pVarSrc*  
 Ukazatel na **VARIANT** objekt, který má být zkopírován do nové `_variant_t` objektu.  
  
 *var_t_Src*  
 A `_variant_t` objekt, který má být zkopírován do nové `_variant_t` objektu.  
  
 `fCopy`  
 Pokud je hodnota false, zadaných **VARIANT** objekt je připojený k nové `_variant_t` objektu bez vytvoření nové kopie podle **VariantCopy**.  
  
 *Kód, sSrc*  
 Celočíselná hodnota, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 `vtSrc`  
 **VARTYPE** pro nové `_variant_t` objektu.  
  
 *fltSrc dblSrc*  
 Číselné hodnoty, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 `cySrc`  
 A **CY** objekt, který má být zkopírován do nové `_variant_t` objektu.  
  
 `bstrSrc`  
 A `_bstr_t` objekt, který má být zkopírován do nové `_variant_t` objektu.  
  
 *strSrc wstrSrc*  
 Řetězec, který se má zkopírovat do nové `_variant_t` objektu.  
  
 `bSrc`  
 A `bool` hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 `pIUknownSrc`  
 Ukazatel rozhraní COM **VT_UNKNOWN** objekt, který má být zapouzdřena do nové `_variant_t` objektu.  
  
 `pDispSrc`  
 Ukazatel rozhraní COM **VT_DISPATCH** objekt, který má být zapouzdřena do nové `_variant_t` objektu.  
  
 `decSrc`  
 A **DECIMAL** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 `bSrc`  
 A **BAJTŮ** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 `cSrc`  
 A `char` hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *usSrc*  
 A **nepodepsané prostě** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *ulSrc*  
 A `unsigned long` hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 `iSrc`  
 `int` Hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *uiSrc*  
 `unsigned int` Hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *i8Src*  
 __**Int64** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *ui8Src*  
 **Nepodepsané __int64** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
## <a name="remarks"></a>Poznámky  
  
-   **(_variant_t)** vytvoří prázdnou `_variant_t` objektu `VT_EMPTY`.  
  
-   **_variant_t (VARIANT &***varSrc***)** vytvoří `_variant_t` objekt z kopie **VARIANT** objektu. Typ varianty se zachová.  
  
-   **_variant_t (VARIANT\****pVarSrc***)** vytvoří `_variant_t` objekt z kopie **VARIANT** objektu. Typ varianty se zachová.  
  
-   **_variant_t (_variant_t &***var_t_Src***)** vytvoří `_variant_t` objekt z jiné `_variant_t` objektu. Typ varianty se zachová.  
  
-   **_variant_t (VARIANT &***varSrc* **, bool**`fCopy`**)** vytvoří `_variant_t` objekt z existující  **VARIANT** objektu. Pokud `fCopy` je **false**, **VARIANT** objekt je připojený k nového objektu bez vytvoření kopie.  
  
-   **_variant_t (krátký***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** vytvoří `_variant_t` objektu typu `VT_I2` nebo `VT_BOOL` z **krátké** celočíselnou hodnotu. Žádné jiné **VARTYPE** vede `E_INVALIDARG` chyby.  
  
-   **_variant_t (dlouho** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** vytvoří `_variant_t` objektu typu `VT_I4`, `VT_BOOL`, nebo `VT_ERROR` z **dlouho** celočíselnou hodnotu. Žádné jiné **VARTYPE** vede `E_INVALIDARG` chyby.  
  
-   **_variant_t (float**`fltSrc`**)** vytvoří `_variant_t` objektu typu `VT_R4` z **float** číselnou hodnotu.  
  
-   **_variant_t (dvojité** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** vytvoří `_variant_t` objektu typu `VT_R8` nebo `VT_DATE` z **dvojité** číselnou hodnotu. Žádné jiné **VARTYPE** vede `E_INVALIDARG` chyby.  
  
-   **_variant_t (CY &**`cySrc`**)** vytvoří `_variant_t` objektu typu `VT_CY` z **CY** objektu.  
  
-   **_variant_t (_bstr_t &**`bstrSrc`**)** vytvoří `_variant_t` objektu typu `VT_BSTR` z `_bstr_t` objektu. Nový `BSTR` je přidělen.  
  
-   **_variant_t (wchar_t \***  *wstrSrc***)** vytvoří `_variant_t` objektu typu `VT_BSTR` z řetězec znaků Unicode. Nový `BSTR` je přidělen.  
  
-   **_variant_t (char\***`strSrc`**)** vytvoří `_variant_t` objektu typu `VT_BSTR` z řetězce. Nový `BSTR` je přidělen.  
  
-   **_variant_t (bool**`bSrc`**)** vytvoří `_variant_t` objektu typu `VT_BOOL` z `bool` hodnotu.  
  
-   **_variant_t (IUnknown\***  `pIUknownSrc` **, bool**`fAddRef`**= true)** vytvoří `_variant_t` objektu typu **VT_UNKNOWN**  z COM rozhraní ukazatel. Pokud `fAddRef` je **true**, pak `AddRef` se volá na ukazatel zadaný rozhraní tak, aby odpovídaly volání **verze** , dojde při `_variant_t` objekt zničena. Je na vás k volání **verze** na ukazatel zadaný rozhraní. Pokud `fAddRef` je **false**, tento konstruktor přijímá vlastnictví ukazatel zadaný rozhraní; Nevolejte **verze** na ukazatel zadaný rozhraní.  
  
-   **_variant_t (IDispatch\***  `pDispSrc` **, bool**`fAddRef`**= true)** vytvoří `_variant_t` objektu typu **VT_DISPATCH**  z COM rozhraní ukazatel. Pokud `fAddRef` je **true**, pak `AddRef` se volá na ukazatel zadaný rozhraní tak, aby odpovídaly volání **verze** , dojde při `_variant_t` objekt zničena. Je na vás k volání **verze** na ukazatel zadaný rozhraní. Pokud **fAddRef** je nastavena hodnota false, trvá tento konstruktor vlastnictví ukazatel zadaný rozhraní; Nevolejte **verze** na ukazatel zadaný rozhraní.  
  
-   **_variant_t (DECIMAL &**`decSrc`**)** vytvoří `_variant_t` objektu typu **VT_DECIMAL** z **DECIMAL** hodnotu.  
  
-   **_variant_t (BYTE**`bSrc`**)** vytvoří `_variant_t` objektu typu `VT_UI1` z **BAJTŮ** hodnotu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)