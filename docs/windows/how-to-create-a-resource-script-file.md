---
title: 'Postupy: Vytvoření souboru skriptu prostředků (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: f3f0adff256742c98a672e40e6b31de9bd7a84ed
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849955"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Postupy: Vytvoření souboru skriptu prostředků (C++)

> [!NOTE]
> **Editor prostředků** není k dispozici ve verzích Express.
>
> Tento materiál se vztahuje na aplikace klasické pracovní plochy Windows. Projekty v jazycích technologie .NET nepoužívají soubory skriptu prostředků. Další informace najdete v tématu [soubory prostředků](../windows/resource-files-visual-studio.md), další informace.

## <a name="to-create-a-new-resource-script-rc-file"></a>Vytvoření nového souboru skriptu prostředků (.rc)

1. Přesuňte fokus na složku existujícího projektu v **Průzkumníka řešení**, například `MyProject`.

   > [!NOTE]
   > Nepleťte si složku projektu se složkou řešení v **Průzkumníka řešení**. Pokud přesunete fokus na **řešení** složka, budou možnosti v **přidat novou položku** dialogové okno (v kroku 3) se bude lišit.

1. Na **projektu** nabídce vyberte možnost **přidat novou položku**.

1. V **přidat novou položku** dialogové okno, vyberte **Visual C++** složky klikněte na tlačítko **soubor prostředků (.rc)** v pravém podokně.

1. Zadejte název souboru skriptu prostředku v **název** textové pole a pak zvolte **otevřít**.

Teď můžete [vytvořit](../windows/how-to-create-a-resource.md) a přidejte nové prostředky do souboru .rc.

> [!NOTE]
> Skript prostředků (soubor .rc) lze přidat pouze do existujícího projektu, který je načten do vývojového prostředí (IDE) pro Visual Studio. Nelze vytvořit samostatný soubor .rc (mimo projekt). [Šablony prostředků](../windows/how-to-use-resource-templates.md) (soubory .rct) lze vytvořit kdykoli.

## <a name="to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>K otevření souboru skriptu prostředků mimo projekt jazyka C++ (samostatný)

Prostředky můžete zobrazit v souboru .rc bez nutnosti otevřít projekt. Otevře se v okně dokumentu na rozdíl od otevřít v souboru .rc [zobrazení prostředků](../windows/resource-view-window.md) okno (stejně jako když je soubor otevřen, uvnitř projektu).

> [!NOTE]
> Jde o důležité odlišení, protože některé příkazy nejsou k dispozici, pouze když je soubor otevřen samostatné (mimo projekt). Například můžete pouze uložení souboru do jiného formátu nebo jako jiný název souboru při otevření souboru mimo projekt ( **uložit jako** příkazu není dostupná, když je soubor otevřen v projektu).

### <a name="to-open-an-rc-file-outside-a-project"></a>Otevřete soubor .rc mimo projekt

1. Z **souboru** nabídce zvolte **otevřít**a pak vyberte **souboru**.

1. V **otevřít soubor** dialogové okno, přejděte do souboru skriptu prostředků, kterou chcete zobrazit, zvýrazněte soubor a vyberte **otevřít**.

   > [!NOTE]
   > Pokud nejprve otevřete projekt (**souboru**, **otevřete**, **projektu**), nebudou mít k dispozici některé příkazy. Otevřít soubor "standalone" znamená otevření bez první načtení projektu.

### <a name="to-open-multiple-rc-files-outside-a-project"></a>K otevření více souborů .rc mimo projekt

1. Otevřete oba samostatné soubory prostředků. Například otevřete `Source1.rc` a `Source2.rc`.

   1. Z **souboru** nabídce zvolte **otevřít**a pak vyberte **souboru**.

   1. V **otevřít soubor** dialogové okno, přejděte do první souboru skriptu prostředků, kterou chcete otevřít (`Source1.rc`), vyberte ho a zvolte možnost **otevřete**.

   1. Opakujte předchozí krok pro druhý .rc soubor otevřít (`Source2.rc`).

       Soubory .rc jsou teď otevřít v systému windows v samostatných dokumentech.

1. Když jsou otevřené oba soubory .rc, dlaždici windows, takže je možné současně zobrazit:

   - Z **okno** nabídce zvolte **Nová vodorovná skupina karet** nebo **Nová svislá skupina karet**.

       \- nebo –

   - Klikněte pravým tlačítkem na jeden ze souborů .rc a zvolte **Nová vodorovná skupina karet** nebo **Nová svislá skupina karet** z místní nabídky.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-open-a-resource-script-file-in-text-format"></a>K otevření souboru skriptu prostředků v textovém formátu

Může nastat situace, kdy budete chtít zobrazit obsah souboru projektu prostředků skriptů (.rc) bez nutnosti otevřít prostředek, jako je například dialogové okno, v jeho editoru konkrétní prostředek. Můžete například hledání řetězce napříč všechna dialogová okna v souboru prostředků, aniž byste museli otevřít každý z nich samostatně.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

Snadno můžete otevřít soubor prostředků v textovém formátu zobrazit všechny prostředky, které obsahuje a dokončete globální operací podporované textového editoru.

> [!NOTE]
> Editory prostředků nečtou přímo .rc nebo `resource.h` soubory. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-as-text"></a>K otevření souboru skriptu prostředků jako text

1. Z **souboru** nabídku zvolte **otevřít**, klikněte na tlačítko **souboru**.

1. V **otevřít soubor** dialogové okno, přejděte do souboru skriptu prostředků, které chcete zobrazit v textovém formátu.

1. Zvýrazněte soubor a pak vyberte šipku rozevíracího seznamu na **otevřít** tlačítko (nachází se na pravé straně tlačítka).

1. Zvolte **otevřít v** z rozevírací nabídky.

1. V **otevřít v** dialogu **Editor zdrojového kódu (textu)**.

1. Z **otevřít jako** rozevíracího seznamu vyberte **Text**.

   Prostředek se otevře v **zdrojový kód** editoru.

\- nebo –

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor .rc.

1. V místní nabídce zvolte **otevřít v programu...** a pak vyberte **Editor zdrojového kódu (textu)**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)