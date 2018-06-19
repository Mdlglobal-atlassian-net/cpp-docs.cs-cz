---
title: Inicializace modulu OLE | Microsoft Docs
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
ms.openlocfilehash: b8224cf27313b056b95990f514e02eb9d9c08cad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374721"
---
# <a name="ole-initialization"></a>Inicializace OLE
Aplikaci mohli používat OLE systémových služeb, musí inicializovat OLE systémové knihovny DLL a ověřte, zda jsou knihovny DLL správnou verzi. **AfxOLEInit –** funkce inicializuje OLE systémové knihovny DLL.  
  
### <a name="ole-initialization"></a>Inicializace OLE  
  
|||  
|-|-|  
|[AfxOLEInit –](#afxoleinit)|Inicializuje knihoven OLE.| 
|[AfxEnableControlContainer –](#afxenablecontrolcontainer)|Volání této funkce do objektu application `InitInstance` funkce povolení podpory pro členství ve skupině ovládacích prvků OLE.| 


## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer –
Volání této funkce do objektu application `InitInstance` funkce povolení podpory pro členství ve skupině ovládacích prvků OLE.  
   
### <a name="syntax"></a>Syntaxe    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>Poznámky  
 Další informace o ovládací prvky OLE (nazývané nyní – ovládací prvky ActiveX) najdete v tématu [témata ovládací prvek ActiveX](../mfc-activex-controls.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  

  
##  <a name="afxoleinit"></a>  AfxOLEInit –  
 Inicializuje podporu technologie OLE pro aplikaci.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová hodnota, pokud je úspěšné. Nula, pokud se nezdaří inicializace, pravděpodobně proto, že jsou nainstalovány nesprávné verze knihoven DLL technologie OLE.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této funkce lze inicializovat podporu technologie OLE pro aplikaci MFC. Při volání této funkce dojde k následujícím akcím:  
  
-   Inicializuje knihovnu modelu COM v aktuálním objektu apartment volající aplikace. Další informace najdete v tématu [provedení](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Vytvoří objekt filtru zpráv implementace [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) rozhraní. Tento filtr zpráv lze přistupovat pomocí volání [afxolegetmessagefilter –](application-control.md#afxolegetmessagefilter).  
  
> [!NOTE]
>  Pokud **AfxOLEInit –** je volána z knihovny MFC DLL volání selže. K selhání dojde, protože funkce předpokládá, že pokud je volána z knihovny DLL, systém technologie OLE byl dříve inicializován volající aplikací.  
  
> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Když zavoláte [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ve vaší `InitInstance` přepsat, zadejte `COINIT_APARTMENTTHREADED` (místo `COINIT_MULTITHREADED`). Další informace najdete v tématu PRB: MFC aplikace přestane reagovat při inicializaci aplikace jako a více vláken typu Apartment (828643) v [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
