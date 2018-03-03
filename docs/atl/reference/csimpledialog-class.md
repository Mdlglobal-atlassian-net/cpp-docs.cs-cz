---
title: "Třída CSimpleDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e497d5f1646ab890b7dafa3e1fb7e1c711a8a09
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csimpledialog-class"></a>CSimpleDialog – třída
Tato třída implementuje základní modální dialogové.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>  
class CSimpleDialog : public CDialogImplBase
```  
  
#### <a name="parameters"></a>Parametry  
 *t_wDlgTemplateID*  
  
 ID prostředku prostředku šablony dialogového okna.  
  
 *t_bCenter*  
 **Hodnota TRUE,** Pokud má být zarovnaný na střed v okně vlastníka; jinak hodnota objektu dialogového okna **FALSE**.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](#domodal)|Vytvoří modální dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 Implementuje modální dialogové okno s základních funkcí. `CSimpleDialog`poskytuje podporu pro běžné ovládací prvky Windows jenom. Vytvoření a zobrazí modální dialogové okno, vytvoření instance této třídy, poskytuje název existující šablony prostředků pro dialogové okno. Pole objektu dialogového okna se zavře po kliknutí na libovolný ovládací prvek s předem definované hodnoty (například IDOK nebo IDCANCEL).  
  
 `CSimpleDialog`Umožňuje vytvořit pouze modálních dialogových oken. `CSimpleDialog`Poskytuje postup pole dialogu, který používá výchozí mapování zpráv směrovat zprávy do příslušné obslužné rutiny.  
  
 V tématu [implementace dialogové okno](../../atl/implementing-a-dialog-box.md) Další informace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="domodal"></a>CSimpleDialog::DoModal  
 Vyvolá modální dialogové okno a vrátí výsledek – dialogové okno po dokončení.  
  
```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Obslužná rutina s nadřazeným dialogového okna. Pokud není zadána žádná hodnota, nadřazený nastavená na aktuální aktivní okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného vrácená hodnota je ID prostředku ovládací prvek, který se zavře dialogové okno.  
  
 Pokud se funkce nezdaří, je vrácenou hodnotu -1. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává všechny interakci s uživatelem, při dialogové okno je aktivní. To je díky modální; dialogových oken To znamená uživatel nemůže komunikovat s jinými dokud nezavře dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
