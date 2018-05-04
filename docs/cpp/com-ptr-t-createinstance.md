---
title: _com_ptr_t::CreateInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70ccd73980295bdda67a4c49d034b6d185d2d93c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance
**Konkrétní Microsoft**  
  
 Vytvoří novou instanci objektu zadané **CLSID** nebo **ProgID**.  
  
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
 `rclsid`  
 **CLSID** objektu.  
  
 `clsidString`  
 Řetězec znaků Unicode, který obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
 `clsidStringA`  
 Vícebajtové řetězce, pomocí ANSI znaková stránka, která obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
 `dwClsContext`  
 Kontext spuštění spustitelného kódu.  
  
 `pOuter`  
 Vnější Neznámý pro [agregace](../atl/aggregation.md).  
  
## <a name="remarks"></a>Poznámky  
 Tyto členské funkce volání `CoCreateInstance` k vytvoření nového objektu COM a pak dotazů pro typ rozhraní tento inteligentní ukazatel. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. **Verze** nazývá se sníží počet odkazů pro dříve zapouzdřené ukazatele. Tato rutina indikuje úspěch nebo neúspěch pomocí hodnoty `HRESULT`.  
  
-   **CreateInstance – (** `rclsid` **,**`dwClsContext`**)** vytvoří novou instanci objektu zadané spuštěné **CLSID**.        
  
-   **CreateInstance – (** `clsidString` **,**`dwClsContext`**)** vytvoří novou instanci objektu zadaný řetězec znaků Unicode, který obsahuje buď spuštěné **CLSID**(počínaje "**{**") nebo **ProgID**.        
  
-   **CreateInstance – (** `clsidStringA` **,**`dwClsContext`**)** vytvoří novou instanci objektu zadané vícebajtový řetězec, který obsahuje buď spuštěné **CLSID**  (počínaje "**{**") nebo **ProgID**.       Volání [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), která předpokládá, že řetězec je v znaková stránka ANSI spíše než znakovou stránku pro výrobce OEM.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)