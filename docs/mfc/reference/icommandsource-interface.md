---
title: Icommandsource – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4908566a80fcad2350023f2306a952b2d97b2e62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060673"
---
# <a name="icommandsource-interface"></a>Icommandsource – rozhraní

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
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Přidá skupinu obslužné rutiny zpráv uživatelské rozhraní příkazů do zdrojového objektu příkazu.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Obslužné rutiny zpráv uživatelské rozhraní příkaz přidá do zdrojového objektu příkazu.|
|[ICommandSource::PostCommand](#postcommand)|Odešle zprávu bez čekání na zpracování.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Obslužná rutina příkazu odebere ze zdrojového objektu příkazu.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Odebere skupinu obslužné rutiny příkazů ze zdrojového objektu příkazu.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Odebere skupinu obslužné rutiny zpráv uživatelské rozhraní příkazů ze zdrojového objektu příkazu.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Obslužná rutina příkazu zprávy uživatelské rozhraní se odebere ze zdrojového objektu příkazu.|
|[ICommandSource::SendCommand](#sendcommand)|Odešle zprávu a čeká na zpracování před vrácením.|

### <a name="remarks"></a>Poznámky

Když hostujete uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací [icommandtarget – rozhraní](../../mfc/reference/icommandtarget-interface.md), poskytnout odkaz na uživatelský ovládací prvek `ICommandSource` objektu.

Zobrazit [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `ICommandTarget`.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Obslužná rutina příkazu přidá do zdrojového objektu příkazu.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.
*cmdHandler*<br/>
Popisovač metody obslužné rutiny příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda přidá cmdHandler obslužná rutina příkazu do zdrojového objektu příkazu a mapuje cmdID obslužné rutiny.
Zobrazit [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat AddCommandHandler.

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

Přidá skupinu obslužné rutiny příkazů do zdrojového objektu příkazu.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.
*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou mapovány příkazy.
### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů do jedné zprávy rutiny a přidá jej do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler

Přidá skupinu obslužné rutiny zpráv uživatelské rozhraní příkazů do zdrojového objektu příkazu.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.
*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou mapovány příkazy.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů do obslužné rutiny zpráv příkaz rozhraní jednoho uživatele a přidá jej do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler

Obslužné rutiny zpráv uživatelské rozhraní příkaz přidá do zdrojového objektu příkazu.
```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.
*cmdUIHandler*<br/>
Popisovač pro metodu obslužné rutiny zpráv příkaz uživatelské rozhraní.

### <a name="remarks"></a>Poznámky

Tato metoda přidá obslužnou rutinu cmdHandler uživatelské rozhraní příkaz zprávy do zdrojového objektu příkazu a mapuje cmdID obslužné rutiny.

## <a name="postcommand"></a> ICommandSource::PostCommand

Odešle zprávu bez čekání na zpracování.
```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
Identifikátor příkazu zprávy, která se má zveřejnit.
### <a name="remarks"></a>Poznámky

Tato metoda asynchronně odešle zprávu mapovat na ID příkaz. Volá CWnd::PostMessage umístí zprávu ve frontě zpráv v okně a vrátí bez čekání na okno odpovídající zprávu.

## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler

Obslužná rutina příkazu odebere ze zdrojového objektu příkazu.
```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.
### <a name="remarks"></a>Poznámky

Tato metoda odstraní obslužná rutina příkazu namapované na cmdID ze zdrojového objektu příkazu.

## <a name="removecommandrangecommandhandler"></a> ICommandSource::RemoveCommandRangeHandler

Odebere skupinu obslužné rutiny příkazů ze zdrojového objektu příkazu.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.
### <a name="remarks"></a>Poznámky

Tato metoda odstraní skupinu z namapované na zadaný příkaz ID cmdIDMin a cmdIDMax, ze zdrojového objektu příkazu obslužné rutiny zpráv.

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler

Odebere skupinu obslužné rutiny zpráv uživatelské rozhraní příkazů ze zdrojového objektu příkazu.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.
### <a name="remarks"></a>Poznámky

Tato metoda odstraní skupinu uživatelské rozhraní příkaz obslužné rutiny zpráv, mapovat na ID zadaný příkaz cmdIDMin a cmdIDMax, ze zdrojového objektu příkazu.

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler

Obslužná rutina příkazu zprávy uživatelské rozhraní se odebere ze zdrojového objektu příkazu.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.
### <a name="remarks"></a>Poznámky

Tato metoda odstraní uživatelské rozhraní zpráva obslužná rutina příkazu namapované na cmdID ze zdrojového objektu příkazu.

## <a name="sendcommand"></a> ICommandSource::SendCommand

Odešle zprávu a čeká na zpracování před vrácením.
```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
Identifikátor příkazu zprávy k odeslání.
### <a name="remarks"></a>Poznámky

Tato metoda synchronně odešle zprávu mapovat na ID příkaz. Volá CWnd::SendMessage umístí zprávu ve frontě zpráv v okně a počká, až tuto proceduru okna zpracovala zpráva před vrácením.
## <a name="see-also"></a>Viz také

[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget – rozhraní](../../mfc/reference/icommandtarget-interface.md)
