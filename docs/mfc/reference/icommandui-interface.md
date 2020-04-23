---
title: ICommandUI – rozhraní
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: b75509beb7287fad5e51dc9d15fc3e47cacf6854
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751305"
---
# <a name="icommandui-interface"></a>ICommandUI – rozhraní

Spravuje příkazy uživatelského rozhraní.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandUI
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[icommandui__Check](#check)|Nastaví položku uživatelského rozhraní pro tento příkaz do příslušného kontrolního stavu.|
|[iCommandUI::ContinueRouting](#continuerouting)|Sděluje mechanismus směrování příkazů, aby pokračoval v směrování aktuální zprávy v řetězci obslužných rutin.|
|[ICommandUI::Povoleno](#enabled)|Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.|
|[ICommandUI::ID](#id)|Získá ID objektu uživatelského rozhraní `ICommandUI` reprezentovaného objektem.|
|[iCommandUI::Index](#index)|Získá index objektu uživatelského rozhraní `ICommandUI` reprezentované ho objektem.|
|[ICommandUI::Rádio](#radio)|Nastaví položku uživatelského rozhraní pro tento příkaz do příslušného kontrolního stavu.|
|[icommandui::Text](#text)|Nastaví text položky uživatelského rozhraní pro tento příkaz.|

## <a name="remarks"></a>Poznámky

Toto rozhraní poskytuje metody a vlastnosti, které spravují příkazy uživatelského rozhraní. `ICommandUI`je podobná [třídě CCmdUI](../../mfc/reference/ccmdui-class.md) `ICommandUI` , s výjimkou, která se používá pro aplikace knihovny MFC, které spolupracují s komponentami .NET.

`ICommandUI`se používá v rámci obslužné rutiny ON_UPDATE_COMMAND_UI v odvozené třídě [ICommandTarget.](../../mfc/reference/icommandtarget-interface.md) Když uživatel aplikace aktivuje (vybere nebo klikne) nabídku, každá položka nabídky se zobrazí jako povolená nebo zakázaná. Cíl každého příkazu nabídky poskytuje tyto informace implementací obslužné rutiny ON_UPDATE_COMMAND_UI. Pro každý z objektů uživatelského rozhraní příkazu v aplikaci vytvořte pomocí [Průvodce třídou](mfc-class-wizard.md) pro každou obslužnou rutinu prototyp položky mapy zpráv a funkce.

Další informace o `ICommandUI` tom, jak je rozhraní používáno v příkazu směrování, naleznete v [tématu Postup: Přidání směrování příkazů do ovládacího prvku Formuláře systému Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Další informace o správě příkazů uživatelského rozhraní v knihovně MFC naleznete v [tématu CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI::Kontrola

Nastaví položku uživatelského rozhraní pro tento příkaz do příslušného kontrolního stavu.

```
property UICheckState Check;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušného kontrolního stavu. Nastavte zkontrolovat na následující hodnoty:

- 0 Zrušit zaškrtnutí
- 1 Kontrola
- 2 Nastavit neurčitý

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>iCommandUI::ContinueRouting

Sděluje mechanismus směrování příkazů, aby pokračoval v směrování aktuální zprávy v řetězci obslužných rutin.

```cpp
void ContinueRouting();
```

## <a name="remarks"></a>Poznámky

Toto je pokročilá členská funkce, která by měla být použita ve spojení s obslužnou rutinou ON_COMMAND_EX, která vrací hodnotu FALSE. Další informace naleznete v tématu Technická poznámka TN006: Mapy zpráv.

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI::Povoleno

Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.

```
property bool Enabled;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz. Nastavte možnost Povoleno na hodnotu TRUE, chcete-li položku povolit, neplatí ji NEPRAVDA.

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI::ID

Získá ID objektu uživatelského rozhraní reprezentované ho objektem ICommandUI.

```
property unsigned int ID;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost získá ID (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiného objektu uživatelského rozhraní reprezentovaného objektem ICommandUI.

## <a name="icommanduiindex"></a><a name="index"></a>iCommandUI::Index

Získá index objektu uživatelského rozhraní reprezentované objektu ICommandUI.

```
property unsigned int Index;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost získá index (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiného objektu uživatelského rozhraní reprezentovaného objektem ICommandUI.

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI::Rádio

Nastaví položku uživatelského rozhraní pro tento příkaz do příslušného kontrolního stavu.

```
property bool Radio;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušného kontrolního stavu. Chcete-li položku povolit, nastavte rádio na hodnotu TRUE; jinak FALSE.

## <a name="icommanduitext"></a><a name="text"></a>icommandui::Text

Nastaví text položky uživatelského rozhraní pro tento příkaz.

```
property String^ Text;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost nastaví text položky uživatelského rozhraní pro tento příkaz. Nastavte text na popisovač textového řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Viz také

[CCmdUI – třída](../../mfc/reference/ccmdui-class.md)
