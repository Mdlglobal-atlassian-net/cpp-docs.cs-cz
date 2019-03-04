---
title: Icommandtarget – rozhraní
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: a224b868ea1923bb4f84b0d682c71fadb63da572
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299927"
---
# <a name="icommandtarget-interface"></a>Icommandtarget – rozhraní

Uživatelský ovládací prvek poskytuje rozhraní pro příjem příkazy ze zdrojového objektu příkazu.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandTarget
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|Inicializuje objekt cílového příkazu.|

## <a name="remarks"></a>Poznámky

Když hostujete uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací `ICommandTarget`, poskytnout odkaz na uživatelský ovládací prvek [rozhraní ICommandSource](../../mfc/reference/icommandsource-interface.md) objektu.

Zobrazit [jak: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `ICommandTarget`.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)

##  <a name="initialize"></a> ICommandTarget::Initialize

Inicializuje objekt cílového příkazu.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Popisovač do zdrojového objektu příkazu.

### <a name="remarks"></a>Poznámky

Když hostujete uživatelského ovládacího prvku v zobrazení knihovny MFC, CWinFormsView směřuje příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC.

Tato metoda inicializuje cílový objekt příkazu a přidruží ji k cmdSource zadaný příkaz zdrojového objektu. By měla být volána v implementaci třídy uživatelského ovládacího prvku. Při inicializaci byste měli zaregistrovat pomocí zdrojového objektu příkazu ve volání ICommandSource::AddCommandHandler v implementaci inicializace obslužné rutiny příkazů. V tématu Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms příklad toho, jak k tomu použít inicializace.

## <a name="see-also"></a>Viz také:

[Postupy: Přidání směrování příkazů do ovládacího prvku modelu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource – rozhraní](../../mfc/reference/icommandsource-interface.md)
