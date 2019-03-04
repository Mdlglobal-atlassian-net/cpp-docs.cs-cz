---
title: Inicializace OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 3d49b37ffc2561fa9a51463a893ec2ba4f4fb725
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304025"
---
# <a name="ole-initialization"></a>Inicializace OLE

Předtím, než aplikace může použít systémových služeb OLE, musí inicializovat OLE systémové knihovny DLL a ověřte, zda správnou verzi knihovny DLL. `AfxOleInit` Funkce inicializuje OLE systémové knihovny DLL.

### <a name="ole-initialization"></a>Inicializace OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicializuje knihoven OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Volejte tuto funkce ve vaší aplikaci objekt `InitInstance` funkce povolení podpory pro členství ve skupině ovládacích prvků OLE.|

## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer

Volejte tuto funkce ve vaší aplikaci objekt `InitInstance` funkce povolení podpory pro členství ve skupině ovládacích prvků OLE.

### <a name="syntax"></a>Syntaxe

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Poznámky

Další informace o ovládacích prvků OLE (nyní nazývá ovládací prvky ActiveX) najdete v tématu [témata ovládacího prvku ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

##  <a name="afxoleinit"></a>  AfxOleInit

Inicializuje podporu technologie OLE pro aplikaci.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je úspěšné. Nula, pokud se nezdaří inicializace, pravděpodobně proto, že jsou nainstalovány nesprávné verze knihoven DLL technologie OLE.

### <a name="remarks"></a>Poznámky

Voláním této funkce lze inicializovat podporu technologie OLE pro aplikaci MFC. Při volání této funkce dojde k následujícím akcím:

- Inicializuje knihovnu modelu COM v aktuálním objektu apartment volající aplikace. Další informace najdete v tématu [OleInitialize](/windows/desktop/api/ole2/nf-ole2-oleinitialize).

- Vytvoří objekt filtru zprávy implementace [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) rozhraní. Tomuto filtru zprávy lze přistupovat pomocí volání [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Pokud **AfxOleInit** je volána z knihovny MFC DLL, volání se nezdaří. K selhání dojde, protože funkce předpokládá, že pokud je volána z knihovny DLL, systém technologie OLE byl dříve inicializován volající aplikací.

> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Při volání [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) ve vašich `InitInstance` přepsání, určete COINIT_APARTMENTTHREADED (spíše než COINIT_MULTITHREADED).

### <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
