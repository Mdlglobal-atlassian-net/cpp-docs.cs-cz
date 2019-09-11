---
title: Rozhraní ICommandUI
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
ms.openlocfilehash: a7bb3ab5ed292cef8108e937e67bc9e2ccc1ebce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907885"
---
# <a name="icommandui-interface"></a>Rozhraní ICommandUI

Spravuje příkazy uživatelského rozhraní.

## <a name="syntax"></a>Syntaxe

```
interface class ICommandUI
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[icommandui__Check](#check)|Nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.|
|[ICommandUI::ContinueRouting](#continuerouting)|Oznamuje mechanismu směrování příkazů, aby pokračoval v směrování aktuální zprávy o řetězu obslužných rutin.|
|[ICommandUI:: Enabled](#enabled)|Povoluje nebo zakazuje položku uživatelského rozhraní pro tento příkaz.|
|[ICommandUI:: ID](#id)|Získá ID objektu uživatelského rozhraní reprezentovaného `ICommandUI` objektem.|
|[ICommandUI:: index](#index)|Získá index objektu uživatelského rozhraní reprezentovaného `ICommandUI` objektem.|
|[ICommandUI:: Radio](#radio)|Nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.|
|[ICommandUI:: text](#text)|Nastaví text položky uživatelského rozhraní pro tento příkaz.|

## <a name="remarks"></a>Poznámky

Toto rozhraní poskytuje metody a vlastnosti, které spravují příkazy uživatelského rozhraní. `ICommandUI`se podobá [třídě CCmdUI –](../../mfc/reference/ccmdui-class.md), s tím `ICommandUI` rozdílem, že se používá pro aplikace MFC, které spolupracují s komponentami .NET.

`ICommandUI`se používá v obslužné rutině ON_UPDATE_COMMAND_UI v třídě odvozené z [ICommandTarget](../../mfc/reference/icommandtarget-interface.md). Když se uživatel aplikace aktivuje (vybere nebo klikne) na nabídku, zobrazí se každá položka nabídky jako povolená nebo zakázaná. Cíl jednotlivých příkazů nabídky poskytuje tyto informace implementací obslužné rutiny ON_UPDATE_COMMAND_UI. Pro každý z objektů uživatelského rozhraní příkazu v aplikaci použijte [Průvodce třídami](mfc-class-wizard.md) k vytvoření položky mapování zpráv a prototypu funkce pro každou obslužnou rutinu.

Další informace o tom, jak `ICommandUI` se rozhraní používá při směrování příkazu, najdete [v tématu How to: Přidejte směrování příkazů do ovládacího prvku](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)model Windows Forms.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Další informace o tom, jak jsou příkazy uživatelského rozhraní spravovány v knihovně MFC, naleznete v tématu [Třída CCmdUI –](../../mfc/reference/ccmdui-class.md).

## <a name="check"></a>ICommandUI:: check

Nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.
```
property UICheckState Check;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly. Nastavte kontrolu na následující hodnoty:
- 0 zrušit kontrolu
- 1 check
- 2 nastavit neurčitelné

## <a name="continuerouting"></a>ICommandUI::ContinueRouting

Oznamuje mechanismu směrování příkazů, aby pokračoval v směrování aktuální zprávy o řetězu obslužných rutin.
```
void ContinueRouting();
```

## <a name="remarks"></a>Poznámky

Toto je pokročilá členská funkce, která by se měla používat ve spojení s obslužnou rutinou ON_COMMAND_EX, která vrací hodnotu FALSE. Další informace najdete v tématu technická Poznámka TN006: Mapy zpráv.

## <a name="enabled"></a>ICommandUI:: Enabled

Povoluje nebo zakazuje položku uživatelského rozhraní pro tento příkaz.
```
property bool Enabled;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost povoluje nebo zakazuje položku uživatelského rozhraní pro tento příkaz. Nastavte na hodnotu TRUE, chcete-li povolit položku, FALSE a zakažte ji.

## <a name="id"></a>ICommandUI:: ID

Získá ID objektu uživatelského rozhraní reprezentovaného objektem ICommandUI.
```
property unsigned int ID;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost získá ID (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiného objektu uživatelského rozhraní reprezentovaného objektem ICommandUI.

## <a name="index"></a>ICommandUI:: index

Získá index objektu uživatelského rozhraní reprezentovaného objektem ICommandUI.
```
property unsigned int Index;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost získá index (popisovač) položky nabídky, tlačítko panelu nástrojů nebo jiný objekt uživatelského rozhraní reprezentovaný objektem ICommandUI.

## <a name="radio"></a>ICommandUI:: Radio

Nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.
```
property bool Radio;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly. Nastavte přepínač na hodnotu TRUE, chcete-li položku Povolit. v opačném případě FALSE.

## <a name="text"></a>ICommandUI:: text

Nastaví text položky uživatelského rozhraní pro tento příkaz.
```
property String^ Text;
```

## <a name="remarks"></a>Poznámky

Tato vlastnost nastavuje text položky uživatelského rozhraní pro tento příkaz. Nastavte text na popisovač textového řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Viz také:

[CCmdUI – třída](../../mfc/reference/ccmdui-class.md)
