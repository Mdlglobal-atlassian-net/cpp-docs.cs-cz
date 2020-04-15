---
title: ICommandTarget – rozhraní
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: 865a8a27d96f84f536e40ec5a7bbbbdd9837dfcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356913"
---
# <a name="icommandtarget-interface"></a>ICommandTarget – rozhraní

Poskytuje uživatelskému ovládacímu prvku rozhraní pro příjem příkazů z objektu zdroje příkazů.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandTarget
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ICommandTarget::Inicializovat](#initialize)|Inicializuje cílový objekt příkazu.|

## <a name="remarks"></a>Poznámky

Když hostujete uživatelský ovládací prvek v zobrazení knihovny MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) směruje příkazy a aktualizuje zprávy uživatelského rozhraní příkazu do uživatelského ovládacího prvku, aby mohl zpracovávat příkazy knihovny MFC (například položky nabídky rámce a tlačítka panelu nástrojů). Implementací `ICommandTarget`můžete dát uživateli ovládací prvek odkaz na [objekt ICommandSource.](../../mfc/reference/icommandsource-interface.md)

Postup: [Přidání příkazu směrování do ovládacího prvku Formuláře systému Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pro příklad použití `ICommandTarget`.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommandTarget::Inicializovat

Inicializuje cílový objekt příkazu.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Úchyt pro objekt zdroje příkazu.

### <a name="remarks"></a>Poznámky

Když hostujete uživatelský ovládací prvek v zobrazení knihovny MFC, CWinFormsView směruje příkazy a aktualizuje zprávy uživatelského rozhraní příkazu do uživatelského ovládacího prvku, aby mohl zpracovávat příkazy knihovny MFC.

Tato metoda inicializuje cílový objekt příkazu a přidruží jej k zadanému objektu zdroje příkazu cmdSource. By měla být volána v implementaci třídy řízení uživatele. Při inicializaci byste měli zaregistrovat obslužné rutiny příkazů s objektem zdroje příkazů voláním ICommandSource::AddCommandHandler v implementaci Initialize. Přečtěte si téma Postup: Přidání příkazu směrování do ovládacího prvku formuláře systému Windows pro příklad, jak použít Inicializovat k tomu.

## <a name="see-also"></a>Viz také

[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource – rozhraní](../../mfc/reference/icommandsource-interface.md)
