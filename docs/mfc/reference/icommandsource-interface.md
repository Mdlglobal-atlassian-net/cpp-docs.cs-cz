---
title: ICommandSource – rozhraní
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
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356978"
---
# <a name="icommandsource-interface"></a>ICommandSource – rozhraní

Spravuje příkazy odeslané z objektu zdroje příkazů do uživatelského ovládacího prvku.

## <a name="syntax"></a>Syntaxe

```cpp
interface class ICommandSource
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iCommandSource::AddCommandHandler](#addcommandhandler)|Přidá obslužnou rutinu příkazu k objektu zdroje příkazů.|
|[iCommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Přidá skupinu obslužných rutin příkazů k objektu zdroje příkazů.|
|[iCommandSource::AddCommandRangeUihandler](#addcommandrangeuihandler)|Přidá skupinu obslužných rutin zpráv příkazu uživatelského rozhraní do objektu zdroje příkazů.|
|[iCommandSource::AddCommandUihandler](#addcommandrangeuihandler)|Přidá obslužnou rutinu zprávy příkazu uživatelského rozhraní do objektu zdroje příkazů.|
|[ICommandSource::PostCommand](#postcommand)|Odešle zprávu bez čekání na její zpracování.|
|[iCommandSource::RemoveCommandHandler](#removecommandhandler)|Odebere obslužnou rutinu příkazu z objektu zdroje příkazů.|
|[iCommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Odebere skupinu obslužných rutin příkazů z objektu zdroje příkazů.|
|[iCommandSource::RemoveCommandRangeUiHandler](#removecommandrangeuihandler)|Odebere skupinu obslužných rutin zpráv příkazů uživatelského rozhraní z objektu zdroje příkazů.|
|[iCommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní z objektu zdroje příkazů.|
|[ICommandSource::Příkaz SendCommand](#sendcommand)|Odešle zprávu a čeká na její zpracování před návratem.|

### <a name="remarks"></a>Poznámky

Když hostujete uživatelský ovládací prvek v zobrazení knihovny MFC, [cWinFormsView Class](../../mfc/reference/cwinformsview-class.md) směruje příkazy a aktualizuje zprávy uživatelského rozhraní příkazu do uživatelského ovládacího prvku, aby mohl zpracovávat příkazy knihovny MFC (například položky nabídky rámce a tlačítka panelu nástrojů). Implementací [iCommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), můžete dát uživatelskému ovládacímu prvku odkaz na `ICommandSource` objekt.

Postup: [Přidání příkazu směrování do ovládacího prvku Formuláře systému Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pro příklad použití `ICommandTarget`.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>iCommandSource::AddCommandHandler

Přidá obslužnou rutinu příkazu k objektu zdroje příkazů.

```cpp
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

Tato metoda přidá příkaz handler cmdHandler do objektu zdroje příkazu a mapuje obslužnou rutinu na cmdID.
Postup: [Přidání příkazu směrování do ovládacího prvku Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití AddCommandHandler.

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>iCommandSource::AddCommandRangeHandler

Přidá skupinu obslužných rutin příkazů k objektu zdroje příkazů.

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazu.
*cmdHandler*<br/>
Popisovač metody obslužné rutiny zprávy, na kterou jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů na jednu obslužnou rutinu zprávy a přidá ji do objektu zdroje příkazu. Používá se pro zpracování skupiny souvisejících tlačítek s jednou metodou.

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>iCommandSource::AddCommandRangeUihandler

Přidá skupinu obslužných rutin zpráv příkazu uživatelského rozhraní do objektu zdroje příkazů.

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazu.
*cmdHandler*<br/>
Popisovač metody obslužné rutiny zprávy, na kterou jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů na obslužnou rutinu zprávy příkazu jednoho uživatelského rozhraní a přidá ji do objektu zdroje příkazu. Používá se pro zpracování skupiny souvisejících tlačítek s jednou metodou.

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>iCommandSource::AddCommandUihandler

Přidá obslužnou rutinu zprávy příkazu uživatelského rozhraní do objektu zdroje příkazů.

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.
*cmdUIHandler*<br/>
Popisovač popisovače příkazu uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Tato metoda přidá příkaz uživatelského rozhraní příkazu rutina cmdHandler do objektu zdroje příkazu a mapuje obslužnou rutinu na cmdID.

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommandSource::PostCommand

Odešle zprávu bez čekání na její zpracování.

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
ID příkazu zprávy, která má být zaúčtována.

### <a name="remarks"></a>Poznámky

Tato metoda asynchronně publikuje zprávu mapovanou na ID určené příkazem. Volá CWnd::PostMessage umístit zprávu do fronty zpráv okna a potom se vrátí bez čekání na odpovídající okno ke zpracování zprávy.

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>iCommandSource::RemoveCommandHandler

Odebere obslužnou rutinu příkazu z objektu zdroje příkazů.

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odebere obslužnou rutinu příkazu mapovanou na cmdID z objektu zdroje příkazu.

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>iCommandSource::RemoveCommandRangeHandler

Odebere skupinu obslužných rutin příkazů z objektu zdroje příkazů.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu obslužných rutin zpráv mapovaných na ID příkazu určené cmdIDMin a cmdIDMax z objektu zdroje příkazu.

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>iCommandSource::RemoveCommandRangeUiHandler

Odebere skupinu obslužných rutin zpráv příkazů uživatelského rozhraní z objektu zdroje příkazů.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.
*cmdIDMax*<br/>
Koncový index rozsahu ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu obslužných rutin zpráv příkazu uživatelského rozhraní mapovaných na ID příkazů určených parametry cmdIDMin a cmdIDMax z objektu zdroje příkazu.

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>iCommandSource::RemoveCommandUIHandler

Odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní z objektu zdroje příkazů.

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní namapovanou na cmdID z objektu zdroje příkazu.

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommandSource::Příkaz SendCommand

Odešle zprávu a čeká na její zpracování před návratem.

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
ID příkazu zprávy, která má být odeslána.

### <a name="remarks"></a>Poznámky

Tato metoda synchronně odešle zprávu mapovanou na ID určené příkazem. Volá CWnd::SendMessage umístit zprávu do fronty zpráv okna a čeká, dokud tento postup okna zpracoval zprávu před vrácením.

## <a name="see-also"></a>Viz také

[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget – rozhraní](../../mfc/reference/icommandtarget-interface.md)
