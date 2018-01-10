---
title: _com_ptr_t::CreateInstance | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::CreateInstance
dev_langs: C++
helpviewer_keywords: CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4764cf615bf04e9f2b1c3c816becc5a58da35f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
-   **CreateInstance – (** `clsidString` **,**`dwClsContext`**)** vytvoří novou instanci objektu zadaný řetězec znaků Unicode, který obsahuje buď spuštěné **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
-   **CreateInstance – (** `clsidStringA` **,**`dwClsContext`**)** vytvoří novou instanci objektu zadané vícebajtový řetězec, který obsahuje buď spuštěné  **CLSID** (počínaje "**{**") nebo **ProgID**. Volání [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), která předpokládá, že řetězec je v znaková stránka ANSI spíše než znakovou stránku pro výrobce OEM.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)