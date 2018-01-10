---
title: "Tlačítko styly | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BS_DEFPUSHBUTTON
- BS_NOTIFY
- BS_MULTILINE
- BS_AUTOCHECKBOX
- BS_3STATE
- BS_BITMAP
- BS_TOP
- BS_PUSHBUTTON
- BS_PUSHLIKE
- BS_AUTO3STATE
- BS_CHECKBOX
- BS_AUTORADIOBUTTON
- BS_RADIOBUTTON
- BS_OWNERDRAW
- BS_LEFT
- BS_USERBUTTON
- BS_RIGHTBUTTON
- BS_RIGHT
- BS_LEFTTEXT
- BS_TEXT
- BS_BOTTOM
- BS_GROUPBOX
- BS_FLAT
- BS_VCENTER
- BS_ICON
- BS_CENTER
dev_langs: C++
helpviewer_keywords:
- BS_NOTIFY constant [MFC]
- BS_RIGHTBUTTON constant [MFC]
- styles [MFC], button objects
- BS_USERBUTTON constant [MFC]
- BS_VCENTER constant [MFC]
- BS_PUSHLIKE constant [MFC]
- BS_RADIOBUTTON constant [MFC]
- BS_PUSHBUTTON constant [MFC]
- BS_DEFPUSHBUTTON constant [MFC]
- BS_LEFTTEXT constant [MFC]
- button objects (CButton), button styles
- BS_AUTO3STATE constant [MFC]
- BS_3STATE constant [MFC]
- BS_OWNERDRAW constant [MFC]
- BS_AUTORADIOBUTTON constant [MFC]
- BS_GROUPBOX constant [MFC]
- BS_BITMAP constant [MFC]
- BS_CENTER constant [MFC]
- BS_MULTILINE constant [MFC]
- BS_BOTTOM constant [MFC]
- BS_FLAT constant [MFC]
- BS_AUTOCHECKBOX constant [MFC]
- BS_RIGHT constant [MFC]
- BS_CHECKBOX constant [MFC]
- BS_LEFT constant [MFC]
- BS_ICON constant [MFC]
- BS_TOP constant [MFC]
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9ed2dcffbcd45215008b3d0caa802a5384367b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="button-styles"></a>Styly tlačítek
Toto téma popisuje typy tlačítko a stylů.  
  
## <a name="button-types"></a>Tlačítko typy  
 Následující tabulka uvádí typy tlačítko. Volitelně můžete vybrat jednu z těchto možností. Pokud nezadáte typ tlačítka, výchozí hodnota je `BS_PUSHBUTTON`.  
  
|Typ|Popis|  
|----------|-----------------|  
|`BS_3STATE`|Vytvoří tlačítko zaškrtávací políčko s tří stavů: `BST_CHECKED`, `BST_INDETERMINATE`, a `BST_UNCHECKED`. Kliknutím na tlačítko odešle `BN_CLICKED` oznámení do okna vlastníka, ale neumožňuje změnit stav tlačítko. Ve výchozím nastavení přidružené text se zobrazí vpravo od pole. Pokud chcete zobrazit text vlevo od pole, použijte `BS_LEFTTEXT` nebo `BS_RIGHTBUTTON` stylu.|  
|`BS_AUTO3STATE`|Vytvoří tlačítko zaškrtávací políčko s tří stavů: `BST_CHECKED`, `BST_INDETERMINATE`, a `BST_UNCHECKED`. Kliknutím na tlačítko odešle `BN_CLICKED` oznámení do okna vlastníka a změní stav tlačítko. Tlačítko stavy cyklu v pořadí podle `BST_CHECKED`, `BST_INDETERMINATE`, a `BST_UNCHECKED`. Ve výchozím nastavení přidružené text se zobrazí vpravo od pole. Pokud chcete zobrazit text vlevo od pole, použijte `BS_LEFTTEXT` nebo `BS_RIGHTBUTTON` stylu.|  
|`BS_AUTOCHECKBOX`|Vytvoří tlačítko zaškrtávací políčko s dvěma stavy: `BST_CHECKED` a `BST_UNCHECKED`. Kliknutím na tlačítko odešle `BN_CLICKED` oznámení do okna vlastníka a změní stav tlačítko. Ve výchozím nastavení přidružené text se zobrazí vpravo od pole. Pokud chcete zobrazit text vlevo od pole, použijte `BS_LEFTTEXT` nebo `BS_RIGHTBUTTON` stylu.|  
|`BS_AUTORADIOBUTTON`|Vytvoří přepínače s dvěma stavy: `BST_CHECKED` a `BST_UNCHECKED`. Přepínací tlačítka se obvykle používají ve skupinách, se všemi skupinami s maximálně jednu možnost zaškrtnuté najednou. Kliknutím na tlačítko odešle `BN_CLICKED` oznámení do okna vlastníka nastaví stav kliknutelnou přepínač na `BST_CHECKED`a nastaví stav všech ostatních tlačítek ve skupině, tlačítko `BST_UNCHECKED`. Ve výchozím nastavení přidružené text se zobrazí vpravo od přepínač. Chcete-li zobrazit text nalevo od přepínač, použijte `BS_LEFTTEXT` nebo `BS_RIGHTBUTTON` stylu.|  
|`BS_CHECKBOX`|Vytvoří tlačítko zaškrtávací políčko s dvěma stavy: `BST_CHECKED` a `BST_UNCHECKED`. Kliknutím na tlačítko odešle `BN_CLICKED` oznámení do okna vlastníka, ale neumožňuje změnit stav tlačítko. Ve výchozím nastavení přidružené text se zobrazí vpravo od pole. Pokud chcete zobrazit text vlevo od pole, použijte `BS_LEFTTEXT` nebo `BS_RIGHTBUTTON` stylu.|  
|`BS_COMMANDLINK`|Vytvoří tlačítko příkaz odkaz. Příkazové tlačítko odkaz je příkazového tlačítka, která je specifická pro [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] který zobrazí zelenou šipku nalevo od hlavního textu a Poznámka pod do hlavního textu. Můžete nastavit pomocí textu Poznámka [CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote).|  
|`BS_DEFCOMMANDLINK`|Vytvoří tlačítko příkaz odkaz. Příkazové tlačítko odkaz je příkazového tlačítka, která je specifická pro [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] který zobrazí zelenou šipku nalevo od hlavního textu a Poznámka pod do hlavního textu. Můžete nastavit pomocí textu Poznámka [CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote). Pokud tlačítka v dialogovém okně, stisknutím klávesy ENTER klíče zasílá `BN_CLICKED` oznámení do dialogového okna i v případě, že tlačítko nemá zaměření pro vstup.|  
|`BS_DEFPUSHBUTTON`|Vytvoří příkazového tlačítka, který má velkou černé ohraničení. Pokud tlačítka v dialogovém okně, stisknutím klávesy ENTER klíče zasílá `BN_CLICKED` oznámení do dialogového okna i v případě, že tlačítko nemá zaměření pro vstup.|  
|`BS_DEFSPLITBUTTON`|Vytvoří tlačítko rozdělení. Tlačítko rozdělení je příkazového tlačítka, která je specifická pro [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] obsahující šipku dolů vedle tlačítka. Když kliknete na tlačítko, je výchozí příkaz provést. Když kliknete na šipku rozevíracího seznamu, zobrazí se další příkazy nabídky. Pokud je tlačítko rozdělení v dialogovém okně, stisknutím klávesy ENTER klíče zasílá `BN_CLICKED` oznámení do dialogového okna i v případě, že tlačítko nemá zaměření pro vstup|  
|`BS_GROUPBOX`|Vytvoří obdélníku, ve které je možné seskupit ostatní tlačítka. Text přidružený tento styl se zobrazí v levém horním rohu obdélníku.|  
|`BS_OWNERDRAW`|Vytvoří tlačítko vykreslované uživatelem. Volání framework `DrawItem` metoda při visual aspektů tlačítko změněna. Tento styl musí být nastavená při použití `CBitmapButton` třídy.|  
|`BS_PUSHBUTTON`|Vytvoří příkazového tlačítka, který odesílá `BN_CLICKED` oznámení do okna vlastníka, když uživatel klikne na tlačítko.|  
|`BS_RADIOBUTTON`|Vytvoří přepínače s dvěma stavy: `BST_CHECKED` a `BST_UNCHECKED`. Přepínací tlačítka se obvykle používají ve skupinách, se všemi skupinami s maximálně jednu možnost zaškrtnuté najednou. Kliknutím na tlačítko odešle `BN_CLICKED` oznámení do okna vlastníka, ale neumožňuje automaticky změnit stav žádné tlačítko ve skupině. Ve výchozím nastavení přidružené text se zobrazí vpravo od přepínač. Chcete-li zobrazit text nalevo od přepínač, použijte `BS_LEFTTEXT` nebo `BS_RIGHTBUTTON` stylu.|  
|`BS_SPLITBUTTON`|Vytvoří tlačítko rozdělení. Tlačítko rozdělení je příkazového tlačítka, která je specifická pro [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] obsahující šipku dolů vedle tlačítka. Když kliknete na tlačítko, je výchozí příkaz provést. Když kliknete na šipku rozevíracího seznamu, zobrazí se další příkazy nabídky.|  
|`BS_USERBUTTON`|Zastaralé, ale zadaná pro kompatibilitu s 16bitové verzích systému Windows. Na základě Win32 aplikace by měly používat `BS_OWNERDRAW` místo.|  
  
## <a name="radio-button-and-check-box-styles"></a>Přepínač a zaškrtávací políčko styly  
 Následující tabulka uvádí stylů, které jsou specifické pro přepínací tlačítka a zaškrtávací políčka. Tyto styly ignorují v všechny ostatní typy tlačítko. Můžete si volitelně vybrat jeden nebo více následujících akcí.  
  
|Styl|Popis|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|V kombinaci s přepínač tlačítka nebo zaškrtávacího políčka styl, zobrazí se text na levé straně políčko nebo přepínač.|  
|`BS_RIGHTBUTTON`|V kombinaci s přepínač tlačítka nebo zaškrtávacího políčka styl, zobrazí se text na levé straně políčko nebo přepínač. Tento styl je stejný jako `BS_LEFTTEXT` stylu.|  
|`BS_PUSHLIKE`|Díky zaškrtávací políčko nebo přepínač vypadají a chovají se jako příkazového tlačítka. Se zobrazí tlačítko při stisknutí tlačítka, pokud je jeho stav `BST_CHECKED`, stisknutí a ztmaven v případě, že je její stav `BST_INDETERMINATE`a vydání, pokud je jeho stav `BST_UNCHECKED`.|  
  
## <a name="text-alignment-styles"></a>Styly zarovnání textu  
 Následující tabulka uvádí možnosti zarovnání vodorovného a svislého textu. Volitelně můžete vybrat jednu z těchto možností.  
  
|Styl|Popis|  
|-----------|-----------------|  
|`BS_LEFT`|Zarovná text v obdélníku tlačítko doleva. Ale pokud je tlačítko zaškrtávací políčko nebo přepínač tlačítko, která nemá `BS_RIGHTBUTTON` styl, je ponechán text zarovnán na pravé straně zaškrtněte políčko nebo přepínač.|  
|`BS_RIGHT`|Pravé zarovnává textu v obdélníku tlačítko. Ale pokud je tlačítko zaškrtávací políčko nebo přepínač tlačítko, která nemá `BS_RIGHTBUTTON` styl, text je zarovnán na pravé straně zaškrtněte políčko nebo přepínač doprava.|  
|`BS_CENTER`|Zarovná na střed textu v obdélníku tlačítko vodorovně.|  
|`BS_TOP`|Umístění textu v horní části rámeček tlačítko.|  
|`BS_BOTTOM`|Umístí text v dolní části rámeček tlačítko.|  
|`BS_VCENTER`|Zarovná na střed textu ve svislém směru v obdélníku tlačítko.|  
  
## <a name="button-content-options"></a>Tlačítka možností obsahu  
 V následující tabulce jsou uvedeny možnosti, které označuje, co se zobrazí v tlačítko. Tlačítko typy, které jenom zobrazit text ignorovat tyto styly. Volitelně můžete vybrat jednu z těchto možností.  
  
|Styl|Popis|  
|-----------|-----------------|  
|`BS_BITMAP`|Určuje, že na tlačítko zobrazí rastrový obrázek.|  
|`BS_ICON`|Určuje, že tlačítko zobrazuje ikonu.|  
|`BS_TEXT`|Určuje, že na tlačítko zobrazí text.|  
  
## <a name="other-options"></a>Další možnosti  
 Následující tabulka uvádí další možnosti, které můžete použít s žádným typem tlačítko. Můžete si volitelně vybrat jeden nebo více následujících akcí.  
  
|Styl|Popis|  
|-----------|-----------------|  
|`BS_FLAT`|Určuje, že tlačítko je dvourozměrná a není vykreslován se výchozí stínováním vytvoření trojrozměrné bitové kopie.|  
|`BS_MULTILINE`|Zabalí text tlačítka na více řádků, pokud je příliš dlouhý, nevejde na jeden řádek v obdélníku tlačítko textový řetězec.|  
|`BS_NOTIFY`|Povolí tlačítko pro odesílání `BN_DBLCLK`, `BN_KILLFOCUS`, a `BN_SETFOCUS` zpráv s oznámením do jeho nadřazeného okna. Všimněte si, že tlačítka Odeslat `BN_CLICKED` oznámení bez ohledu na to, zda je zadán tento styl.|  
  
## <a name="see-also"></a>Viz také  
 [Styly využívané prostředím MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create) [tlačítko styly](http://msdn.microsoft.com/library/windows/desktop/bb775951)   



