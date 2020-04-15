---
title: Inicializace OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 39a6f28bfe38f254f15f441ed6305daa2cb5793e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373036"
---
# <a name="ole-initialization"></a>Inicializace OLE

Předtím, než může aplikace používat systémové služby OLE, musí inicializovat knihovny DLL systému OLE a ověřit, zda jsou knihovny DLL správnou verzí. Funkce `AfxOleInit` inicializuje knihovny DLL systému OLE.

### <a name="ole-initialization"></a>Inicializace OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicializuje knihovny OLE.|
|[Kontejner AfxEnableControlContainer](#afxenablecontrolcontainer)|Volání této funkce ve `InitInstance` funkci objektu aplikace povolit podporu pro uzavření ovládacích prvků OLE.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>Kontejner AfxEnableControlContainer

Volání této funkce ve `InitInstance` funkci objektu aplikace povolit podporu pro uzavření ovládacích prvků OLE.

### <a name="syntax"></a>Syntaxe

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Poznámky

Další informace o ovládacích prvcích OLE (nyní nazývaných ovládací prvky ActiveX) naleznete [v tématu Témata ovládacího prvku ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit

Inicializuje podporu technologie OLE pro aplikaci.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je úspěšné. Nula, pokud se nezdaří inicializace, pravděpodobně proto, že jsou nainstalovány nesprávné verze knihoven DLL technologie OLE.

### <a name="remarks"></a>Poznámky

Voláním této funkce lze inicializovat podporu technologie OLE pro aplikaci MFC. Při volání této funkce dojde k následujícím akcím:

- Inicializuje knihovnu modelu COM v aktuálním objektu apartment volající aplikace. Další informace naleznete v tématu [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Vytvoří objekt filtru zpráv, který implementuje rozhraní [IMessageFilter.](/windows/win32/api/objidl/nn-objidl-imessagefilter) Tento filtr zprávy lze přistupovat s voláním [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
> Pokud **AfxOleInit** je volána z knihovny DLL knihovny MFC, volání se nezdaří. K selhání dojde, protože funkce předpokládá, že pokud je volána z knihovny DLL, systém technologie OLE byl dříve inicializován volající aplikací.

> [!NOTE]
> Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Pokud zavoláte [CoInitializeExV](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) v `InitInstance` přepsání, zadejte COINIT_APARTMENTTHREADED (spíše než COINIT_MULTITHREADED).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
