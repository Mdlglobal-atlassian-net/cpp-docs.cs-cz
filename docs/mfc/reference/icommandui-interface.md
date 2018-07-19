---
title: Icommandui – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 244853c3e0e8e16e3de59017b04fb17e64b8efac
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338354"
---
# <a name="icommandui-interface"></a>Icommandui – rozhraní
Slouží ke správě uživatelských rozhraní příkazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[icommandui__Check](#check)|Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.|  
|[ICommandUI::ContinueRouting](#continuerouting)|Určuje mechanismus směrování příkazů pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.|  
|[ICommandUI::Enabled](#enabled)|Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.|  
|[ICommandUI::ID](#id)|Získá ID rozhraní objekt uživatele reprezentován `ICommandUI` objektu.|  
|[ICommandUI::Index](#index)|Získá index rozhraní objekt uživatele reprezentován `ICommandUI` objektu.|  
|[ICommandUI::Radio](#radio)|Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.|  
|[ICommandUI::Text](#text)|Nastaví text položku uživatelského rozhraní pro tento příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní poskytuje metody a vlastnosti, které spravují uživatelských rozhraní příkazů. `ICommandUI` je podobný [ccmdui – třída](../../mfc/reference/ccmdui-class.md), s tím rozdílem, že `ICommandUI` se používá pro aplikace knihovny MFC, které spolupracují s komponent architektury .NET.  
  
 `ICommandUI` se používá v rámci obslužné rutiny ON_UPDATE_COMMAND_UI v [rozhraní ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-odvozené třídy. Když uživatel aplikace aktivuje (zaškrtne nebo kliknutí) nabídka, každá položka nabídky se zobrazí jako povolené nebo zakázané. Cíl každý příkaz nabídky poskytuje tyto informace pomocí implementace obslužné rutiny ON_UPDATE_COMMAND_UI. Pro každý z objektů příkaz uživatelského rozhraní v aplikaci použijte okno Vlastnosti vytvořit položku mapování zpráv a prototyp funkce pro každou obslužnou rutinu.  
  
 Další informace o tom, jak `ICommandUI` rozhraní se používá v směrování příkazů, naleznete v tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Další informace o jak se spravují uživatelských rozhraní příkazů v knihovně MFC, naleznete v tématu [ccmdui – třída](../../mfc/reference/ccmdui-class.md).  
  
## <a name="check"></a> ICommandUI::Check  
Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.
```
property UICheckState Check;
```
## <a name="remarks"></a>Poznámky  
Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Kontrola nastavení následující hodnoty:  
- Zrušte zaškrtnutí 0  
- Kontrola 1  
- Nastavte neurčitý 2  

## <a name="continuerouting"></a> ICommandUI::ContinueRouting   
Určuje mechanismus směrování příkazu pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.
```
void ContinueRouting();
```
## <a name="remarks"></a>Poznámky
To je funkce členů s pokročilým členstvím, které byste měli použít ve spojení s ON_COMMAND_EX obslužná rutina, která vrací hodnotu FALSE. Další informace najdete v tématu Technická poznámka TN006: mapy zpráv.

## <a name="enabled"></a> ICommandUI::Enabled 
Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.
```
property bool Enabled;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz. Nastavit povoleno na hodnotu PRAVDA, povolte položku, FALSE pro jeho zakázání.

## <a name="id"></a> ICommandUI::ID  
Získá ID objektu uživatelské rozhraní icommandui – objektem.
```
property unsigned int ID;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost získá ID (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiný uživatel rozhraní objekt reprezentovaný objektem icommandui –.

## <a name="index"></a> ICommandUI::Index   
Získá index reprezentovaný objektem icommandui – rozhraní objektu uživatele.
```
property unsigned int Index;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost získá index (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiný uživatel rozhraní objekt reprezentovaný objektem icommandui –.

## <a name="radio"></a> ICommandUI::Radio 
Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.
```
property bool Radio;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Nastavte přepínač na true pro povolení položky; v opačném případě FALSE.

## <a name="text"></a> ICommandUI::Text 
Nastaví text položku uživatelského rozhraní pro tento příkaz.
```
property String^ Text;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost nastavuje vlastnost text položky uživatelského rozhraní pro tento příkaz. Nastavte vlastnost Text na popisovač řetězce textu.

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)  
  
## <a name="see-also"></a>Viz také  
 [CCmdUI – třída](../../mfc/reference/ccmdui-class.md)
