---
title: _variant_t::_variant_t | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14386e737d136b91f8864eeaa182038b62df72e0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947536"
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
**Specifické pro Microsoft**  
  
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
 A `VARIANT` objektu, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *pVarSrc*  
 Ukazatel `VARIANT` objektu, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *var_t_Src*  
 A `_variant_t` objektu, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *fCopy*  
 Pokud **false**, zadané `VARIANT` objektu se připojit k novému `_variant_t` objektu bez provedení pomocí nové kopie `VariantCopy`.  
  
 *Kód, sSrc*  
 Celočíselná hodnota, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *vtSrc*  
 `VARTYPE` Pro novou `_variant_t` objektu.  
  
 *fltSrc, dblSrc*  
 Číselné hodnoty, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *cySrc*  
 A `CY` objektu, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *bstrSrc*  
 A `_bstr_t` objektu, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *strSrc wstrSrc*  
 Řetězec, které se mají zkopírovat do nové `_variant_t` objektu.  
  
 *bSrc*  
 A **bool** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *pIUknownSrc*  
 Ukazatele rozhraní modelu COM na objekt VT_UNKNOWN zapouzdřit do nové `_variant_t` objektu.  
  
 *pDispSrc*  
 Ukazatele rozhraní modelu COM na objekt VT_DISPATCH zapouzdřit do nové `_variant_t` objektu.  
  
 *decSrc*  
 A `DECIMAL` hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *bSrc*  
 A `BYTE` hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *cSrc*  
 A **char** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *usSrc*  
 A **unsigned short** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *ulSrc*  
 A **unsigned long** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *Kód*  
 **Int** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *uiSrc*  
 **Unsigned int** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *i8Src*  
 __**Int64** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
 *ui8Src*  
 **Unsigned __int64** hodnota, která má být zkopírován do nové `_variant_t` objektu.  
  
## <a name="remarks"></a>Poznámky  
  
-   **_variant_t – ()** vytvoří prázdnou `_variant_t` objektu, `VT_EMPTY`.  
  
-   **_variant_t – (VARIANT &***varSrc***)** sestaví `_variant_t` objekt z kopie `VARIANT` objektu.     Typ varianty se zachová.  
  
-   **_variant_t – (VARIANT\****pVarSrc***)** sestaví `_variant_t` objekt z kopie `VARIANT` objektu.     Typ varianty se zachová.  
  
-   **_variant_t – (_variant_t &***var_t_Src***)** sestaví `_variant_t` objektu z jiného `_variant_t` objektu.     Typ varianty se zachová.  
  
-   **_variant_t – (VARIANT &***varSrc* **, bool**`fCopy`**)** sestaví `_variant_t` objekt z existující `VARIANT` objekt.       Pokud `fCopy` je **false**, **VARIANT** objekt je připojen nový objekt bez vytvoření kopie.  
  
-   **_variant_t – (krátký***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** sestaví `_variant_t` objekt typu VT_I2 nebo VT_BOOL z **krátký** celočíselnou hodnotu.       Jakýkoli jiný `VARTYPE` způsobí chybu E_INVALIDARG.  
  
-   **_variant_t – (long** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** vytvoří `_variant_t` objekt typu VT_I4, VT_BOOL nebo VT_ERROR z **dlouhý**  celočíselnou hodnotu.       Jakýkoli jiný `VARTYPE` způsobí chybu E_INVALIDARG.  
  
-   **_variant_t – (float**`fltSrc`**)** sestaví `_variant_t` objekt typu VT_R4 z **float** číselnou hodnotu.      
  
-   **_variant_t – (double** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** sestaví `_variant_t` objekt typu VT_R8 nebo VT_DATE z **double** číselnou hodnotu.       Jakýkoli jiný `VARTYPE` způsobí chybu E_INVALIDARG.  
  
-   **_variant_t – (kr &**`cySrc`**)** vytvoří `_variant_t` objekt typu VT_CY z `CY` objektu.      
  
-   **_variant_t – (_bstr_t &**`bstrSrc`**)** sestaví `_variant_t` objekt typu VT_BSTR z `_bstr_t` objektu.     Nový `BSTR` je přidělen.  
  
-   **_variant_t – (wchar_t \***  *wstrSrc***)** sestaví `_variant_t` objekt typu VT_BSTR z řetězce Unicode.   Nový `BSTR` je přidělen.  
  
-   **_variant_t – (char\***`strSrc`**)** sestaví `_variant_t` objekt typu VT_BSTR z řetězce.     Nový `BSTR` je přidělen.  
  
-   **_variant_t – (bool**`bSrc`**)** sestaví `_variant_t` objekt typu VT_BOOL z **bool** hodnotu.      
  
-   **_variant_t – (IUnknown\***  `pIUknownSrc` **, bool**`fAddRef`**= true)** sestaví `_variant_t` objekt typu VT_UNKNOWN z ukazatele rozhraní modelu COM .       Pokud `fAddRef` je **true**, pak `AddRef` je volán na ukazatel zadané rozhraní tak, aby odpovídaly volání `Release` , dojde při `_variant_t` objekt zničen. Je na vás volat `Release` na ukazatel zadané rozhraní. Pokud `fAddRef` je **false**, tento konstruktor přijímá vlastnictví ukazatele zadané rozhraní; Nevolejte `Release` na ukazatel zadané rozhraní.  
  
-   **_variant_t – (IDispatch\***  `pDispSrc` **, bool**`fAddRef`**= true)** sestaví `_variant_t` objekt typu VT_DISPATCH z rozhraní modelu COM ukazatel.       Pokud `fAddRef` je **true**, pak `AddRef` je volán na ukazatel zadané rozhraní tak, aby odpovídaly volání `Release` , dojde při `_variant_t` objekt zničen. Je na vás volat `Release` na ukazatel zadané rozhraní. Pokud `fAddRef` je **false**, tento konstruktor přijímá vlastnictví ukazatele zadané rozhraní; Nevolejte `Release` na ukazatel zadané rozhraní.  
  
-   **_variant_t – (DESÍTKOVÉ &**`decSrc`**)** sestaví `_variant_t` objekt typu VT_DECIMAL z `DECIMAL` hodnotu.      
  
-   **_variant_t – (BYTE**`bSrc`**)** vytvoří `_variant_t` objekt typu `VT_UI1` z `BYTE` hodnotu.      
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)