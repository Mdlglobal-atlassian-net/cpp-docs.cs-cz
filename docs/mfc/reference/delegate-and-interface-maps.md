---
title: "Delegát a rozhraní mapování makra (MFC) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9767c8b92316ffb9e458ba650e28db9ddf1a095b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
|||  
|-|-|  
|[BEGIN_DELEGATE_MAP –](#begin_delegate_map)|Zahájí mapu delegáta.|
|[BEGIN_INTERFACE_MAP –](#begin_interface_map)|Zahájí definici připojený mapy.|
|[Commandhandler – delegát](#commandhandler)|Zaregistruje zpětné volání metody se příkaz zdroj.  |
|[END_DELEGATE_MAP –](#end_delegate_map)|Ukončí mapu delegáta.|
|[END_INTERFACE_MAP –](#end_interface_map)|Ukončí mapy rozhraní v souboru implementace. |
|[EVENT_DELEGATE_ENTRY –](#event_delegate_entry)|Vytvoří položku v mapě delegáta.|
|[INTERFACE_PART –](#interface_part)|Použít mezi `BEGIN_INTERFACE_MAP` makro a `END_INTERFACE_MAP` makro u každého rozhraní objektu bude podporovat.|
|[MAKE_DELEGATE –](#make_delegate)|Připojí do ovládacího prvku spravované obslužné rutiny události.|


## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP –
Zahájí mapu delegáta.  
   
### <a name="syntax"></a>Syntaxe    
```  
BEGIN_DELEGATE_MAP(  CLASS );  
```
### <a name="parameters"></a>Parametry  
 `CLASS`  
 Třída, ve kterém je hostovaná spravované ovládací prvek.  
   
### <a name="remarks"></a>Poznámky  
 Toto makro označuje začátek seznam položek delegáta, které tvoří mapu delegáta. Příklad použití této makro, naleznete v části [EVENT_DELEGATE_ENTRY –](#event_delegate_entry).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** msclr\event.h  
   
### <a name="see-also"></a>Viz také  
 [Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)
 
##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP –
Zahájí definici připojený mapy při použití v souboru implementace.  
   
### <a name="syntax"></a>Syntaxe    
```
BEGIN_INTERFACE_MAP( theClass, baseClass )  
```
### <a name="parameters"></a>Parametry  
 `theClass`  
 Třída, ve kterém má být definován mapy rozhraní  
  
 `baseClass`  
 Třídu, ze které `theClass` je odvozena z.  
   
### <a name="remarks"></a>Poznámky  
 U každého rozhraní, která je implementována, je jeden nebo více `INTERFACE_PART` makro volání. Pro každý agregaci, která používá třídu, existuje jedno **INTERFACE_AGGREGATE** makro volání.  
  
 Další informace o rozhraní mapy, najdete v části [Technická poznámka 38](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
 
##  <a name="commandhandler"></a>Commandhandler – delegát
Zaregistruje zpětné volání metody se příkaz zdroj.  
   
### <a name="syntax"></a>Syntaxe    
```  
delegate void CommandHandler(  UINT^ cmdID  );  
```
### <a name="parameters"></a>Parametry  
 `cmdID`  
 ID příkazu.  
   
### <a name="remarks"></a>Poznámky  
 Tento delegát registruje metody zpětného volání příkazu zdroj. Když přidáte delegáta ke zdrojovému objektu příkaz, stane se metoda zpětného volání obslužné rutiny pro příkazy přicházející ze zadaného zdroje.  
  
 Další informace najdete v tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  
   
### <a name="see-also"></a>Viz také  
 [Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)
 
##  <a name="commanduihandler"></a>Commanduihandler –
Zaregistruje zpětné volání metody se zprávou příkazu update uživatelské rozhraní.  
   
### <a name="syntax"></a>Syntaxe    
```  
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);  
```
### <a name="parameters"></a>Parametry  
 `cmdID`  
 ID příkazu.  
  
 `cmdUI`  
 ID příkazu zprávy.  
   
### <a name="remarks"></a>Poznámky  
 Tento delegát zaregistruje zpětné volání metody se zprávou příkazu uživatelské rozhraní aktualizace. `CommandUIHandler`je podobná [commandhandler –](#commandhandler) s tím rozdílem, že tento delegát je použít s příkazy aktualizace objektů uživatelského rozhraní. Příkazy aktualizace uživatelského rozhraní by měly být namapované 1: 1 pomocí metody obslužné rutiny zpráv.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  
   
### <a name="see-also"></a>Viz také  
 [Postupy: Přidání příkaz prvku směrování do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [CommandHandler](#commandhandler)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP –
Ukončí mapu delegáta.  
   
### <a name="syntax"></a>Syntaxe    
```  
END_DELEGATE_MAP();  
```  
   
### <a name="remarks"></a>Poznámky  
 Toto makro označuje konec seznamu položek delegáta, které tvoří mapu delegáta. Příklad použití této makro, naleznete v části [EVENT_DELEGATE_ENTRY –](#event_delegate_entry).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** msclr\event.h  
   
### <a name="see-also"></a>Viz také  

 [Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

 
##  <a name="end_interface_map"></a>END_INTERFACE_MAP –
Ukončí mapy rozhraní v souboru implementace.  
   
### <a name="syntax"></a>Syntaxe    
```
END_INTERFACE_MAP( )    
```  
   
### <a name="remarks"></a>Poznámky  
 Další informace o mapování rozhraní najdete v tématu [Technická poznámka 38](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [BEGIN_INTERFACE_MAP –](#begin_interface_map)
 

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY –
Vytvoří položku v mapě delegáta.  
   
### <a name="syntax"></a>Syntaxe    
```  
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);  
```
### <a name="parameters"></a>Parametry  
 `MEMBER`  
 Obslužná rutina události být připojené k ovládacímu prvku.  
  
 `ARG0`  
 První argument funkce spravovaná obslužná rutina události, jako například **objekt ^**.  
  
 `ARG1`  
 Druhý argument spravovaná obslužná rutina události, jako například **EventArgs ^**.  
   
### <a name="remarks"></a>Poznámky  
 Každá položka v mapě delegáta odpovídá delegáta obslužné rutiny spravovaného události vytvořené [MAKE_DELEGATE –](#make_delegate).  
   
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `EVENT_DELEGATE_ENTRY` vytvořit položku v mapě delegáta pro `OnClick` obslužné rutiny události; také najdete v příkladu v `MAKE_DELEGATE`. Další informace najdete v tématu [postup: jímky událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).  
  
 ```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()

```  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** msclr\event.h  
   
### <a name="see-also"></a>Viz také  
 [MAKE_DELEGATE –](#make_delegate)   
 [BEGIN_DELEGATE_MAP –](#begin_delegate_map)   
 [END_DELEGATE_MAP –](#end_delegate_map)
 

##  <a name="interface_part"></a>INTERFACE_PART –
Použít mezi `BEGIN_INTERFACE_MAP` makro a `END_INTERFACE_MAP` makro u každého rozhraní objektu bude podporovat.  
   
### <a name="syntax"></a>Syntaxe    
```
INTERFACE_PART( theClass, iid, localClass)  
```
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy, která obsahuje mapy rozhraní.    
 `iid`  
 Identifikátory IID, který se má namapovat k třídě embedded.    
 *localClass*  
 Název třídy místní.  
   
### <a name="remarks"></a>Poznámky  
 Umožňuje mapovat IID členem třídy indikován `theClass` a *localClass*.  
  
 Další informace o rozhraní mapy, najdete v části [Technická poznámka 38](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
   
 
##  <a name="make_delegate"></a>MAKE_DELEGATE –
Připojí do ovládacího prvku spravované obslužné rutiny události.  
   
### <a name="syntax"></a>Syntaxe    
```  
MAKE_DELEGATE( DELEGATE,  MEMBER) ;  
```
### <a name="parameters"></a>Parametry  
 `DELEGATE`  
 Typ obslužné rutiny spravovaného události delegovat, jako například [obslužná rutina události](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).  
  
 `MEMBER`  
 Název metody obslužné rutiny události být připojené k ovládacímu prvku.  
   
### <a name="remarks"></a>Poznámky  
 Toto makro vytvoří delegáta obslužné rutiny událostí spravovaného typu `DELEGATE` a názvu `MEMBER`. Delegát obslužná rutina události spravované umožňuje nativních tříd pro zpracování spravovaného události.  
   
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak volat `MAKE_DELEGATE` připojit `OnClick` obslužné rutiny události pro ovládací prvek MFC `MyControl`. Širší vysvětlení, jak tento makro funguje v aplikaci MFC najdete v tématu [postup: jímky událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).  
  
```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** msclr\event.h  
   
### <a name="see-also"></a>Viz také  
 [BEGIN_DELEGATE_MAP –](#begin_delegate_map)   
 [END_DELEGATE_MAP –](#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY –](#event_delegate_entry)
 



