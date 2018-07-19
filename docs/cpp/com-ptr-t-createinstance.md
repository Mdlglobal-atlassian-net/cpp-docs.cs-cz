---
title: _com_ptr_t::CreateInstance | Dokumentace Microsoftu
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
ms.openlocfilehash: c8aca9422c4798cd798d048ce42443c4f38bd170
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947597"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance
**Specifické pro Microsoft**  
  
 Vytvoří novou instanci objektu dle `CLSID` nebo `ProgID`.  
  
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
 *rclsid*  
 `CLSID` Objektu.  
  
 *clsidString*  
 Řetězec znaků Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.  
  
 *clsidStringA*  
 Vícebajtový řetězec používající znakovou stránku ANSI, který udržuje `CLSID` (počínaje "**{**") nebo `ProgID`.  
  
 *dwClsContext*  
 Kontext spuštění spustitelného kódu.  
  
 *pOuter*  
 Vnější Neznámá pro [agregace](../atl/aggregation.md).  
  
## <a name="remarks"></a>Poznámky  
 Tyto členské funkce volají `CoCreateInstance` k vytvoření nového objektu modelu COM a pak dotazů pro typ rozhraní tohoto inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel. Tato rutina vrátí hodnotu HRESULT indikuje úspěch nebo selhání.  
  
-   **Funkci CreateInstance (***rclsid* **,***dwClsContext***)** vytvoří novou běžící instanci objektu dle `CLSID`.        
  
-   **Funkci CreateInstance (***clsidString* **,***dwClsContext***)** vytvoří novou běžící instanci objektu dle Řetězec znaků Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.        
  
-   **Funkci CreateInstance (***clsidStringA* **,***dwClsContext***)** vytvoří novou běžící instanci objektu dle vícebajtový řetězec udržující `CLSID` (počínaje "**{**") nebo `ProgID`.       Volání [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), kde se předpokládá, že je řetězec uložen ve znakovou stránku ANSI, nikoli znakovou stránku OEM.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)