---
title: _com_ptr_t::GetActiveObject | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 392460cde35096bc1c61db4d7e6bd2143932838d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403992"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Specifické pro Microsoft**  
  
 Připojí se k existující instanci objektu dle `CLSID` nebo `ProgID`.  
  
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
 *rclsid*  
 `CLSID` Objektu.  
  
 *clsidString*  
 Řetězec znaků Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.  
  
 *clsidStringA*  
 Vícebajtový řetězec používající znakovou stránku ANSI, který udržuje `CLSID` (počínaje "**{**") nebo `ProgID`.  
  
## <a name="remarks"></a>Poznámky  
 Tyto členské funkce volají **GetActiveObject** níž načítají ukazatel na spuštěný objekt registrovaný technologií OLE a potom dotazy pro tohoto inteligentního ukazatele typu rozhraní. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel. Tato rutina vrátí hodnotu HRESULT indikuje úspěch nebo selhání.  
  
-   **GetActiveObject (**`rclsid`**)** připojí k existující instanci objektu dle `CLSID`.  
  
-   **GetActiveObject (**`clsidString`**)** připojí k existující instanci objektu dle řetězce Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.  
  
-   **GetActiveObject (**`clsidStringA`**)** připojí k existující instanci objektu dle vícebajtového řetězce znaků obsahujícího `CLSID` (počínaje "**{**") nebo `ProgID`. Volání [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), kde se předpokládá, že je řetězec uložen ve znakovou stránku ANSI, nikoli znakovou stránku OEM.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)