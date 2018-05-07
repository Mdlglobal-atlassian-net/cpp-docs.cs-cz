---
title: Rozhraní ICommandUI | Microsoft Docs
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
ms.openlocfilehash: 70e6f1eb8848c5ee93063877ae036f66584b69c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icommandui-interface"></a>ICommandUI rozhraní
Spravovat příkazů uživatelského rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[icommandui__Check](#check)|Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.|  
|[ICommandUI::ContinueRouting](#continuerouting)|Informuje mechanismus směrování příkazů pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.|  
|[ICommandUI::Enabled](#enabled)|Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.|  
|[ICommandUI::ID](#id)|Získá ID objektu uživatelské rozhraní reprezentována `ICommandUI` objektu.|  
|[ICommandUI::Index](#index)|Získá index rozhraní objekt uživatele reprezentován `ICommandUI` objektu.|  
|[ICommandUI::Radio](#radio)|Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.|  
|[ICommandUI::Text](#text)|Nastaví text položku uživatelského rozhraní pro tento příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní poskytuje metody a vlastnosti, které spravovat příkazů uživatelského rozhraní. `ICommandUI` je podobná [CCmdUI – třída](../../mfc/reference/ccmdui-class.md)kromě toho, že `ICommandUI` se používá pro aplikace MFC, které spolupracovat s součásti rozhraní .NET.  
  
 `ICommandUI` se používá v rámci `ON_UPDATE_COMMAND_UI` obslužné rutiny v [rozhraní ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-odvozené třídy. Když uživatel aplikace aktivuje (vybere nebo klikne na) nabídky, každá položka nabídky se zobrazí jako povolené nebo zakázané. Cíl pro každý příkaz nabídky implementací poskytuje tyto informace `ON_UPDATE_COMMAND_UI` obslužné rutiny. Okno Vlastnosti pro každý z objektů příkaz uživatelského rozhraní v aplikaci, lze použijte k vytvoření mapy zpráv položku a funkce prototypu pro každou obslužnou rutinu.  
  
 Další informace o tom, jak `ICommandUI` rozhraní se používá v směrování příkazů najdete v tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Další informace o tom, jak se spravují příkazy uživatelského rozhraní v MFC najdete v tématu [CCmdUI – třída](../../mfc/reference/ccmdui-class.md).  
  
## <a name="check"></a> ICommandUI::Check  
Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.
```
property UICheckState Check;
```
## <a name="remarks"></a>Poznámky  
Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Zkontrolujte nastavení na následující hodnoty:  
- Zrušte zaškrtnutí 0  
- Kontrola 1  
- Nastavit neurčitém 2  

## <a name="continuerouting"></a> ICommandUI::ContinueRouting   
Určuje příkaz mechanismus směrování pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.
```
void ContinueRouting();
```
## <a name="remarks"></a>Poznámky
Toto je k pokročilé – členská funkce, která se používá ve spojení s on_command_ex – obslužná rutina, která vrátí hodnotu FALSE. Další informace najdete v tématu technické Poznámka TN006: mapy zpráv.

## <a name="enabled"></a> ICommandUI::Enabled 
Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.
```
property bool Enabled;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz. Nastavit povoleno na hodnotu true, aby položky FALSE ji zakázat.

## <a name="id"></a> ICommandUI::ID  
Získá ID uživatele rozhraní objektu představovaného objektem ICommandUI.
```
property unsigned int ID;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost získá ID (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiného uživatele objektu rozhraní reprezentovaný objektem ICommandUI.

## <a name="index"></a> ICommandUI::Index   
Získá index reprezentovaný objektem ICommandUI rozhraní objektu uživatele.
```
property unsigned int Index;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost získá index (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiného uživatele objektu rozhraní reprezentovaný objektem ICommandUI.

## <a name="radio"></a> ICommandUI::Radio 
Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.
```
property bool Radio;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Nastavení přepínačů na hodnotu true, aby položka; jinak hodnota FALSE.

## <a name="text"></a> ICommandUI::Text 
Nastaví text položku uživatelského rozhraní pro tento příkaz.
```
property String^ Text;
```
## <a name="remarks"></a>Poznámky
Tato vlastnost nastaví text položku uživatelského rozhraní pro tento příkaz. Nastavit Text do textového řetězce popisovače.

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  
  
## <a name="see-also"></a>Viz také  
 [CCmdUI – třída](../../mfc/reference/ccmdui-class.md)
