---
title: Inicializace OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 6860697dd3adbe26197dd9075e84f402029e00a5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855684"
---
# <a name="ole-initialization"></a>Inicializace OLE

Předtím, než může aplikace používat systémové služby OLE, musí inicializovat systémové knihovny DLL OLE a ověřit, zda jsou knihovny DLL správné verze. Funkce `AfxOleInit` inicializuje systémové knihovny DLL systému OLE.

### <a name="ole-initialization"></a>Inicializace OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicializuje knihovny OLE.|
|[AfxEnableControlContainer –](#afxenablecontrolcontainer)|Voláním této funkce ve funkci `InitInstance` vašeho objektu aplikace povolíte podporu pro omezení ovládacích prvků OLE.|

## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer –

Voláním této funkce ve funkci `InitInstance` vašeho objektu aplikace povolíte podporu pro omezení ovládacích prvků OLE.

### <a name="syntax"></a>Syntaxe

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Poznámky

Další informace o ovládacích prvcích OLE (nyní označovaných jako ovládací prvky ActiveX) najdete v tématu [témata ovládacího prvku ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="afxoleinit"></a>AfxOleInit

Inicializuje podporu technologie OLE pro aplikaci.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je úspěšné. Nula, pokud se nezdaří inicializace, pravděpodobně proto, že jsou nainstalovány nesprávné verze knihoven DLL technologie OLE.

### <a name="remarks"></a>Poznámky

Voláním této funkce lze inicializovat podporu technologie OLE pro aplikaci MFC. Při volání této funkce dojde k následujícím akcím:

- Inicializuje knihovnu modelu COM v aktuálním objektu apartment volající aplikace. Další informace najdete v tématu [OleInitialize selhal](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Vytvoří objekt filtru zpráv, který implementuje rozhraní [IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter) . K tomuto filtru zpráv je možné připomenout pomocí volání [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Pokud je volána metoda **AfxOleInit** z knihovny MFC DLL, volání se nezdaří. K selhání dojde, protože funkce předpokládá, že pokud je volána z knihovny DLL, systém technologie OLE byl dříve inicializován volající aplikací.

> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Pokud zavoláte [funkce CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) v přepsání `InitInstance`, zadejte COINIT_APARTMENTTHREADED (místo COINIT_MULTITHREADED).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
