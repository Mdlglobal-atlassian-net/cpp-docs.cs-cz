---
title: "Rozhraní ICommandSource | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
dev_langs:
- C++
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc8ad34ccce059caca8e86a014622e29c14022ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="icommandsource-interface"></a>ICommandSource rozhraní
Spravuje příkazy, odeslané ze zdrojového objektu příkazu do uživatelského ovládacího prvku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class ICommandSource  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Obslužná rutina příkazu přidá do zdrojového objektu příkazu.|  
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Přidá skupinu obslužné rutiny příkazů do zdrojového objektu příkazu.|  
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Přidá skupinu obslužné rutiny zpráv uživatelské rozhraní příkaz zdrojovým objektem příkaz.|  
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Obslužné rutiny zpráv uživatelské rozhraní příkaz přidá do zdrojového objektu příkazu.|  
|[ICommandSource::PostCommand](#postcommand)|Odešle zprávu bez čekání na zpracování.|  
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Obslužná rutina příkazu odebere ze zdrojového objektu příkazu.|  
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Odebere skupinu obslužné rutiny příkazů ze zdrojového objektu příkazu.|  
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Odebere skupinu obslužné rutiny zpráv uživatelské rozhraní příkaz z ke zdrojovému objektu příkazu.|  
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Obslužné rutiny zpráv uživatelské rozhraní příkaz odebere ke zdrojovému objektu příkazu.|  
|[ICommandSource::SendCommand](#sendcommand)|Odešle zprávu a čeká na zpracování před vrácením.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hostitelem uživatelský ovládací prvek v zobrazení knihovny MFC [CWinFormsView třída](../../mfc/reference/cwinformsview-class.md) příkazy trasy a aktualizace příkaz zprávy uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací [rozhraní ICommandTarget rozhraní](../../mfc/reference/icommandtarget-interface.md), poskytněte odkaz na uživatelský ovládací prvek `ICommandSource` objektu.  
  
 V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití `ICommandTarget`.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  
  
## <a name="addcommandhandler"></a>ICommandSource::AddCommandHandler
Obslužná rutina příkazu přidá do zdrojového objektu příkazu.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry  
`cmdID`  
ID příkazu.  
`cmdHandler`  
Popisovač metody obslužná rutina příkazu.

### <a name="remarks"></a>Poznámky
Tato metoda se zdrojovým objektem příkaz přidá cmdHandler obslužná rutina příkazu a obslužná rutina se mapuje na cmdID.
V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití AddCommandHandler.

## <a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Přidá skupinu obslužné rutiny příkazů do zdrojového objektu příkazu.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>Parametry  
`cmdIDMin`  
Index začátek rozsahu ID příkazu.
`cmdIDMax`  
Koncová index rozsah ID příkazu.
`cmdHandler`  
Popisovač pro metodu zpráva obslužná rutina, ke které jsou namapované příkazy.
### <a name="remarks"></a>Poznámky
Tato metoda mapuje souvislý rozsah ID příkazů do jedné zprávy rutiny a přidá ji do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.

## <a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler
Přidá skupinu obslužné rutiny zpráv uživatelské rozhraní příkaz zdrojovým objektem příkaz.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parametry  
`cmdIDMin`  
Index začátek rozsahu ID příkazu.
`cmdIDMax`  
Koncová index rozsah ID příkazu.
`cmdHandler`  
Popisovač pro metodu zpráva obslužná rutina, ke které jsou namapované příkazy.

### <a name="remarks"></a>Poznámky
Tato metoda mapuje souvislý rozsah ID příkazů obslužné rutiny zpráv příkaz rozhraní jednoho uživatele a přidá ji do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.

## <a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler
Obslužné rutiny zpráv uživatelské rozhraní příkaz přidá do zdrojového objektu příkazu.
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parametry
`cmdID`  
ID příkazu.  
`cmdUIHandler`  
Popisovač pro metodu uživatelské rozhraní příkaz zpráva obslužné rutiny.

### <a name="remarks"></a>Poznámky
Tato metoda přidá uživatelské rozhraní příkaz zpráva obslužná rutina cmdHandler ke zdrojovému objektu příkazu a obslužná rutina se mapuje na cmdID.

## <a name="postcommand"></a>ICommandSource::PostCommand
Odešle zprávu bez čekání na zpracování.
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>Parametry
`command`  
Identifikátor příkazu zprávy odesílat.
### <a name="remarks"></a>Poznámky
Tato metoda asynchronně odešle zprávu mapovat na ID zadané pomocí příkazu. Volá CWnd::PostMessage umístit zprávy ve frontě zpráv okna a potom se vrátí bez čekání na okno odpovídající ke zpracování zprávy.


## <a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler
Obslužná rutina příkazu odebere ze zdrojového objektu příkazu.
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parametry
`cmdID`  
ID příkazu.
### <a name="remarks"></a>Poznámky
Tato metoda odebere obslužná rutina namapovaná na cmdID ze zdrojového objektu příkazu.


## <a name="removecommandrangecommandhandler"></a>ICommandSource::RemoveCommandRangeHandler 
Odebere skupinu obslužné rutiny příkazů ze zdrojového objektu příkazu.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parametry
`cmdIDMin`  
Index začátek rozsahu ID příkazu.
`cmdIDMax`  
Koncová index rozsah ID příkazu.
### <a name="remarks"></a>Poznámky
Tato metoda Odebere skupinu obslužné rutiny zpráv namapované na zadaný ID příkaz cmdIDMin a cmdIDMax, ze zdrojového objektu příkazu.

## <a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler 
Odebere skupinu obslužné rutiny zpráv uživatelské rozhraní příkaz z ke zdrojovému objektu příkazu.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parametry
`cmdIDMin`  
Index začátek rozsahu ID příkazu.
`cmdIDMax`  
Koncová index rozsah ID příkazu.
### <a name="remarks"></a>Poznámky
Tato metoda Odebere skupinu uživatelské rozhraní příkaz obslužné rutiny zpráv, namapovaný na zadaný ID příkaz cmdIDMin a cmdIDMax, ze zdrojového objektu příkazu.

## <a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler 
Obslužné rutiny zpráv uživatelské rozhraní příkaz odebere ke zdrojovému objektu příkazu.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parametry
`cmdID`  
ID příkazu.
### <a name="remarks"></a>Poznámky
Tato metoda odebere namapované na cmdID ze zdrojového objektu příkaz popisovač zpráv příkaz uživatelské rozhraní.

## <a name="sendcommand"></a>ICommandSource::SendCommand 
Odešle zprávu a čeká na zpracování před vrácením.
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>Parametry
`command`  
ID příkazu k odeslání zprávy.
### <a name="remarks"></a>Poznámky
Tato metoda synchronně odešle zprávu mapovat na ID zadané pomocí příkazu. Volá CWnd::SendMessage umístit zprávy ve frontě zpráv okna a čeká na zprávu postupu okno zpracovala před vrácením.
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání příkaz prvku směrování do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget – rozhraní](../../mfc/reference/icommandtarget-interface.md)
