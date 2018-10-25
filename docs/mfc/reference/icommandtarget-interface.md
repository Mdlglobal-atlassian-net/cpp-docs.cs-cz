---
title: Icommandtarget – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee8a4bb3f80d9776aec4fd7a6af0d1523c60064d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066081"
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

Zobrazit [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `ICommandTarget`.

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

Tato metoda inicializuje cílový objekt příkazu a přidruží ji k cmdSource zadaný příkaz zdrojového objektu. By měla být volána v implementaci třídy uživatelského ovládacího prvku. Při inicializaci byste měli zaregistrovat pomocí zdrojového objektu příkazu ve volání ICommandSource::AddCommandHandler v implementaci inicializace obslužné rutiny příkazů. V tématu Postupy: přidání směrování příkazů do ovládacího prvku Windows Forms příklad toho, jak k tomu použít inicializace.

## <a name="see-also"></a>Viz také

[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource – rozhraní](../../mfc/reference/icommandsource-interface.md)

