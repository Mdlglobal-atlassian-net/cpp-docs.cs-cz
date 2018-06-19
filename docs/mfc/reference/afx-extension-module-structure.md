---
title: AFX_EXTENSION_MODULE – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6560bf337f6e146bba19e41d56727945df771dd2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349253"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE – struktura
`AFX_EXTENSION_MODULE` Je během inicializace MFC – rozšiřující knihovny DLL používané pro udržení stav rozšíření MFC DLL – modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct AFX_EXTENSION_MODULE  
{  
    BOOL bInitialized;  
    HMODULE hModule;  
    HMODULE hResource;  
    CRuntimeClass* pFirstSharedClass;  
    COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *bInitialized*  
 **Hodnota TRUE,** Pokud byl inicializován modulu DLL `AfxInitExtensionModule`.  
  
 `hModule`  
 Určuje popisovač modul knihovny DLL.  
  
 *hResource*  
 Určuje popisovač modul vlastní prostředek knihovny DLL.  
  
 *pFirstSharedClass*  
 Odkaz na informace ( `CRuntimeClass` struktura) o první třídě runtime modulu DLL. Používá k zajištění začátek seznamu tříd modulu runtime.  
  
 *pFirstSharedFactory*  
 Ukazatel na modulu DLL první objekt pro vytváření ( `COleObjectFactory` objekt). Používá k zajištění začátek seznamu objekt pro vytváření tříd.  
  
## <a name="remarks"></a>Poznámky  
 MFC – rozšiřující knihovny DLL je potřeba udělat dvě věci v jejich `DllMain` funkce:  
  
-   Volání [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) a zkontrolujte návratovou hodnotu.  
  
-   Vytvoření **CDynLinkLibrary** objektu, pokud bude export knihovny DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekty nebo má svou vlastní vlastní prostředky.  
  
 `AFX_EXTENSION_MODULE` Struktura se používá pro uložení kopie rozšíření MFC DLL modulu stavu, včetně kopie runtime třídy objektů, které byly inicializovány rozšíření MFC DLL jako součást normální statický objekt konstrukce spuštěny před `DllMain` je byl zadán. Příklad:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 Modul informace uložené v `AFX_EXTENSION_MODULE` struktura je možné zkopírovat do **CDynLinkLibrary** objektu. Příklad:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule –](extension-dll-macros.md#afxinitextensionmodule)   
 [AfxTermExtensionModule –](extension-dll-macros.md#afxtermextensionmodule)

