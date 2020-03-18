---
title: Rozhraní rozhraní ICommandSource
ms.date: 03/27/2019
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
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: a57ca6f36546a17b9a35ebea875ff01b43de1332
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445709"
---
# <a name="icommandsource-interface"></a>Rozhraní rozhraní ICommandSource

Spravuje příkazy odesílané ze zdrojového objektu příkazu do uživatelského ovládacího prvku.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandSource
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Rozhraní ICommandSource:: AddCommandHandler](#addcommandhandler)|Přidá obslužnou rutinu příkazu do zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: AddCommandRangeHandler](#addcommandrangehandler)|Přidá skupinu obslužných rutin příkazu do zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: AddCommandRangeUIHandler](#addcommandrangeuihandler)|Přidá skupinu obslužných rutin zpráv příkazu uživatelského rozhraní do zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: AddCommandUIHandler](#addcommandrangeuihandler)|Přidá do zdrojového objektu příkazu obslužnou rutinu zprávy příkazu uživatelského rozhraní.|
|[Rozhraní ICommandSource::P ostCommand](#postcommand)|Odešle zprávu bez čekání na zpracování.|
|[Rozhraní ICommandSource:: RemoveCommandHandler](#removecommandhandler)|Odebere obslužnou rutinu příkazu ze zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: RemoveCommandRangeHandler](#removecommandrangehandler)|Odebere skupinu obslužných rutin příkazů ze zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Odebere skupinu obslužných rutin zpráv příkazu uživatelského rozhraní ze zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: RemoveCommandUIHandler](#removecommandrangeuihandler)|Odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní ze zdrojového objektu příkazu.|
|[Rozhraní ICommandSource:: SendCommand](#sendcommand)|Před vrácením pošle zprávu a počká, než se zpracuje.|

### <a name="remarks"></a>Poznámky

Při hostování uživatelského ovládacího prvku v zobrazení knihovny MFC, [třídy CWinFormsView](../../mfc/reference/cwinformsview-class.md) směrují příkazy a zprávy uživatelského rozhraní příkazu k ovládacímu prvku, aby umožnily zpracování příkazů MFC (například položky nabídky rámce a tlačítka panelu nástrojů). Implementací [rozhraní ICommandTarget](../../mfc/reference/icommandtarget-interface.md)udělíte uživatelskému ovládacímu prvku odkaz na objekt `ICommandSource`.

Příklad použití `ICommandTarget`naleznete v tématu [How to: Add Routing and Command to a model Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) .

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>Rozhraní ICommandSource:: AddCommandHandler

Přidá obslužnou rutinu příkazu do zdrojového objektu příkazu.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu
*cmdHandler*<br/>
Popisovač metody obslužné rutiny příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda přidá obslužnou rutinu příkazu cmdHandler do zdrojového objektu příkazu a mapuje obslužnou rutinu na cmdID.
Příklad použití AddCommandHandler najdete v tématu [How to: Add Routing and Command to a model Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) .

## <a name="addcommandrangehandler"></a>Rozhraní ICommandSource:: AddCommandRangeHandler

Přidá skupinu obslužných rutin příkazu do zdrojového objektu příkazu.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů
*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou příkazy mapovány.
### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů na jednu obslužnou rutinu zpráv a přidá ji do zdrojového objektu příkazu. Slouží ke zpracování skupiny souvisejících tlačítek s jednou metodou.

## <a name="addcommandrangeuihandler"></a>Rozhraní ICommandSource:: AddCommandRangeUIHandler

Přidá skupinu obslužných rutin zpráv příkazu uživatelského rozhraní do zdrojového objektu příkazu.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů
*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů na obslužnou rutinu zprávy příkazu jediného uživatelského rozhraní a přidá ji do zdrojového objektu příkazu. Slouží ke zpracování skupiny souvisejících tlačítek s jednou metodou.

## <a name="addcommanduihandler"></a>Rozhraní ICommandSource:: AddCommandUIHandler

Přidá do zdrojového objektu příkazu obslužnou rutinu zprávy příkazu uživatelského rozhraní.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu
*cmdUIHandler*<br/>
Popisovač metody obslužné rutiny zprávy příkazu uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Tato metoda přidá do zdrojového objektu příkazu obslužnou rutinu zprávy příkazu uživatelského rozhraní cmdHandler a mapuje obslužnou rutinu na cmdID.

## <a name="postcommand"></a>Rozhraní ICommandSource::P ostCommand

Odešle zprávu bez čekání na zpracování.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*systému*<br/>
ID příkazu zprávy, která má být odeslána.
### <a name="remarks"></a>Poznámky

Tato metoda asynchronně odesílá zprávu namapovanou na ID určené příkazem. Volá CWnd::P ostMessage umístit zprávu do fronty zpráv v okně a pak se vrátí bez čekání na odpovídající okno ke zpracování zprávy.

## <a name="removecommandhandler"></a>Rozhraní ICommandSource:: RemoveCommandHandler

Odebere obslužnou rutinu příkazu ze zdrojového objektu příkazu.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu
### <a name="remarks"></a>Poznámky

Tato metoda odebere obslužnou rutinu příkazu namapovanou na cmdID ze zdrojového objektu příkazu.

## <a name="removecommandrangehandler"></a>Rozhraní ICommandSource:: RemoveCommandRangeHandler

Odebere skupinu obslužných rutin příkazů ze zdrojového objektu příkazu.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů
### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu obslužných rutin zpráv mapovaných na ID příkazů zadaných pomocí cmdIDMin a cmdIDMax ze zdrojového objektu příkazu.

## <a name="removecommandrangeuihandler"></a>Rozhraní ICommandSource:: RemoveCommandRangeUIHandler

Odebere skupinu obslužných rutin zpráv příkazu uživatelského rozhraní ze zdrojového objektu příkazu.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů
### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu obslužných rutin zpráv příkazu uživatelského rozhraní, které jsou mapovány na ID příkazů určené parametrem cmdIDMin a cmdIDMax, ze zdrojového objektu příkazu.

## <a name="removecommanduihandler"></a>Rozhraní ICommandSource:: RemoveCommandUIHandler

Odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní ze zdrojového objektu příkazu.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu
### <a name="remarks"></a>Poznámky

Tato metoda odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní namapovanou na cmdID ze zdrojového objektu příkazu.

## <a name="sendcommand"></a>Rozhraní ICommandSource:: SendCommand

Před vrácením pošle zprávu a počká, než se zpracuje.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*systému*<br/>
ID příkazu zprávy, která se má odeslat
### <a name="remarks"></a>Poznámky

Tato metoda synchronně odesílá zprávu namapovanou na ID určené příkazem. Volá CWnd:: SendMessage k umístění zprávy do fronty zpráv v okně a počká, dokud tento proces okna před vrácením nezpracovává zprávu.
## <a name="see-also"></a>Viz také

[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget – rozhraní](../../mfc/reference/icommandtarget-interface.md)
