---
title: 'Postupy: zahrnutí prostředků v době kompilace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
dev_langs:
- C++
helpviewer_keywords:
- compiling source code, including resources
- comments [C++], compiled files
- resources [Visual Studio], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 856d448b096910c322750eccc7447689b08b328e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571333"
---
# <a name="how-to-include-resources-at-compile-time"></a>Postupy: Zahrnutí prostředků v čase kompilace
Obvykle je snadný a pohodlný pro práci s výchozí uspořádání všech prostředků v jednom souboru prostředku skriptů (.rc). Ale můžete přidat prostředky v jiných souborech do aktuálního projektu v době kompilace v jejich uvedení v seznamu **směrnice času kompilace** pole [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md).  
  
 Tady je několik důvodů umístit prostředky do souboru než hlavní .rc souborů:  
  
-   Chcete-li přidat komentáře pro příkazy prostředků, které nebudou se odstraní při ukládání souboru .rc.  
  
     Editory prostředků přímo číst soubory .rc nebo souboru resource.h. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc.  
  
-   Chcete zahrnout prostředky, které již byly vývoji a testování a není nutné další změny. (Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.)  
  
-   Chcete zahrnout prostředky, které se používají v několika různých projektech, nebo jsou součástí systému správy verzí zdrojového kódu a tedy musí existovat v centrálním umístění, kde změny bude mít vliv na všechny projekty.  
  
-   Chcete zahrnout prostředky (jako jsou například prostředky RCDATA), které jsou ve vlastním formátu. RCDATA prostředky mohou mít zvláštní požadavky. Například nelze použít výraz jako hodnotu pro pole nameID. Zobrazit [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] Další informace naleznete v dokumentaci.  
  
 Pokud máte oddíly v existujících souborech .rc, které splňují kterákoli z těchto podmínek, měli byste umístit v oddílech v jednom nebo více samostatných souborů .rc a zahrnout je do projektu pomocí [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md). *Projectname*.rc2 soubor vytvořený v podadresáři \res nový projekt se používá pro tento účel.  
  
### <a name="to-include-resources-in-your-project-at-compile-time"></a>Chcete zahrnout prostředky ve vašem projektu v době kompilace  
  
1.  Umístíte prostředky v souboru skriptu prostředků s jedinečným názvem souboru. Nepoužívejte *projectname*.rc, protože to je název souboru pro soubor skriptu prostředku hlavní.  
  
2.  Klikněte pravým tlačítkem na soubor .rc (v [zobrazení prostředků](../windows/resource-view-window.md)) a zvolte **prostředek zahrnuje** z místní nabídky.  
  
3.  V **směrnice času kompilace** přidejte [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivy kompilátoru zahrnout nový soubor prostředků hlavního souboru prostředku ve vývojovém prostředí.  
  
     Prostředky v souborech tímto způsobem jsou součástí vašeho spustitelného souboru k v době kompilace. Nejsou přímo k dispozici pro úpravy nebo změny při práci na souboru .rc hlavního projektu. Budete muset otevřít soubory zahrnuté .rc odděleně. Všechny soubory, které jsou zahrnuty, ale nemají příponou .rc nebude možné upravovat podle editory prostředků.  
  
## <a name="requirements"></a>Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)