---
title: AFX_EXTENSION_MODULE – struktura
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: ee39fcec3083145dbc23c7739897bf89d47578a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539032"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE – struktura

`AFX_EXTENSION_MODULE` Se používá během inicializace MFC – rozšiřující knihovny DLL pro uložení stavu modulu MFC DLL rozšíření.

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

*bInitialized*<br/>
Hodnota TRUE, pokud modul knihovny DLL byl inicializován s `AfxInitExtensionModule`.

*hModule*<br/>
Určuje popisovač modul knihovny DLL.

*hResource*<br/>
Určuje popisovač modul vlastní prostředek knihovny DLL.

*pFirstSharedClass*<br/>
Ukazatel na informace ( `CRuntimeClass` struktury) o první třídy modulu runtime modul knihovny DLL. Používá k poskytování začátku seznamu tříd modulu runtime.

*pFirstSharedFactory*<br/>
Ukazatel na modulu DLL první objekt pro vytváření ( `COleObjectFactory` objekt). Používá k poskytování začátku seznamu objekt pro vytváření tříd.

## <a name="remarks"></a>Poznámky

MFC – rozšiřující knihovny DLL je potřeba udělat dvě věci v jejich `DllMain` funkce:

- Volání [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) a ověřte návratovou hodnotu.

- Vytvoření `CDynLinkLibrary` objektu, pokud se Export knihovny DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekty nebo má svůj vlastní vlastní prostředky.

`AFX_EXTENSION_MODULE` Struktura se používá pro uložení kopie MFC – rozšiřující knihovnu DLL modulu stavu, včetně kopírování objektů tříd modulu runtime, které byly inicializovány pomocí MFC – rozšiřující knihovny DLL jako součást normální statický objekt konstrukce spuštěny před `DllMain` je zadat. Příklad:

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

Informace o modulu uložené v `AFX_EXTENSION_MODULE` struktura je možné zkopírovat do `CDynLinkLibrary` objektu. Příklad:

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)

