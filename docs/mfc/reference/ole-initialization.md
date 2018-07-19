---
title: Inicializace OLE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 330701c4fcc75d40e782d25baa55044b88852f50
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337790"
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
 **Záhlaví:** afxdisp.h  

  
##  <a name="afxoleinit"></a>  AfxOleInit  
 Inicializuje podporu technologie OLE pro aplikaci.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová hodnota, pokud je úspěšné. Nula, pokud se nezdaří inicializace, pravděpodobně proto, že jsou nainstalovány nesprávné verze knihoven DLL technologie OLE.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této funkce lze inicializovat podporu technologie OLE pro aplikaci MFC. Při volání této funkce dojde k následujícím akcím:  
  
-   Inicializuje knihovnu modelu COM v aktuálním objektu apartment volající aplikace. Další informace najdete v tématu [OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Vytvoří objekt filtru zprávy implementace [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) rozhraní. Tomuto filtru zprávy lze přistupovat pomocí volání [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
> [!NOTE]
>  Pokud **AfxOleInit** je volána z knihovny MFC DLL, volání se nezdaří. K selhání dojde, protože funkce předpokládá, že pokud je volána z knihovny DLL, systém technologie OLE byl dříve inicializován volající aplikací.  
  
> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Při volání [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ve vašich `InitInstance` přepsání, určete COINIT_APARTMENTTHREADED (spíše než COINIT_MULTITHREADED). Další informace najdete v tématu PRB: aplikace MFC přestane reagovat při inicializaci aplikace jako a s více vlákny typu Apartment (828643) na [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
