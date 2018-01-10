---
title: _com_ptr_t::GetActiveObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::GetActiveObject
dev_langs: C++
helpviewer_keywords: GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a67d571c2e5b80eaa1c095cc517872b8e3918fd6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Konkrétní Microsoft**  
  
 Připojí k existující instanci objekt daný **CLSID** nebo **ProgID**.  
  
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
 `rclsid`  
 **CLSID** objektu.  
  
 `clsidString`  
 Řetězec znaků Unicode, který obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
 `clsidStringA`  
 Vícebajtové řetězce, pomocí ANSI znaková stránka, která obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
## <a name="remarks"></a>Poznámky  
 Tyto členské funkce volají funkci `GetActiveObject`, pomocí níž načítají ukazatel na spuštěný objekt registrovaný technologií OLE a poté se dotazují na typ rozhraní tohoto inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. **Verze** nazývá se sníží počet odkazů pro dříve zapouzdřené ukazatele. Tato rutina indikuje úspěch nebo neúspěch pomocí hodnoty `HRESULT`.  
  
-   **Getactiveobject – (**`rclsid`**)** připojí k existující instanci objekt daný **CLSID**.  
  
-   **Getactiveobject – (**`clsidString`**)** připojí k existující instanci objekt daný řetězec znaků Unicode, který obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
-   **Getactiveobject – (**`clsidStringA`**)** připojí k existující instanci objekt daný vícebajtový řetězec, který obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**. Volání [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), která předpokládá, že řetězec je v znaková stránka ANSI spíše než znakovou stránku pro výrobce OEM.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)