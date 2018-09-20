---
title: Dynamické rozložení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08fc6f6a5b93851468d412e34b3ee0a85ab534e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413247"
---
# <a name="dynamic-layout"></a>Dynamické rozložení

S knihovnou MFC v sadě Visual Studio 2015 můžete vytvořit dialogová okna, která uživatel může změnit velikost a můžete řídit způsob, jakým upraví rozložení pro změnu velikosti. Například můžete připojit tlačítek v dolní části dialogového okna na dolní okraj tak, aby zůstaly vždy v dolní části. Některé ovládací prvky, jako je například textová pole, rozevírací seznamy a editboxes můžete také nastavit na rostoucí je uživatel rozbalí dialogového okna.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Zadání nastavení dynamické rozložení dialogového okna knihovny MFC

Když uživatel změní dialogové okno, ovládacích prvků v dialogovém okně můžete změnit velikost nebo ve směru X a Y. Změna velikosti nebo pozice ovládacího prvku, když uživatel změní dialogové okno se nazývá dynamické rozložení. Například následující je dialogové okno před během změny velikosti:

![Dialogové okno před během změny velikosti. ](../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")

Po změně šířky, oblasti listbox je zvýšena na Zobrazit další položky a tlačítka se přesouvají společně s pravém dolním rohu:

![Dialogové okno po změně šířky. ](../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")

Dynamické rozložení můžete řídit tak, že zadáte podrobnosti pro každý ovládací prvek v editoru prostředků v prostředí IDE, nebo to můžete provést sestavují programově díky přístupu `CMFCDynamicLayout` objekt pro konkrétní ovládací prvek a nastavení vlastností.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Nastavení vlastností dynamických rozložení v editoru prostředků

Dynamické rozložení chování pro dialogové okno můžete nastavit bez nutnosti psát jakýkoli kód, pomocí editoru prostředků.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Chcete-li nastavit vlastnosti dynamického rozložení v editoru prostředků

1. Pomocí projektu knihovny MFC otevřený otevřete dialogové okno, které chcete pracovat v editoru dialogového okna.

     ![V editoru prostředků, otevřete dialogové okno. ](../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")

2. Vyberte ovládací prvek a v okně Vlastnosti nastavte jeho vlastnosti dynamické rozložení. **Dynamické rozložení** oddíl v okně Vlastnosti obsahuje vlastnosti **přesunutí typu**, **typ velikosti**a v závislosti na vybraných pro tyto vlastnosti hodnot specifické vlastnosti, které definují, kolik ovládacích prvků, přesunout nebo změnit velikost. **Typ posunutí** Určuje, jak se přesune ovládací prvek při změně velikost dialogového okna; **Typ velikosti** Určuje, jak ovládací prvek svou velikost podle velikosti dialogového okna se změní. **Typ posunutí** a **typ velikosti** může být **vodorovné**, **svislé**, **obě**, nebo **žádný**v závislosti na rozměrech, které chcete změnit dynamicky. Dimenze X; je vodorovně Je směru osy Y.

3. Pokud chcete ovládací prvek, jako je například tlačítko bude na pevné velikosti a zůstat na místě v pravém dolním rohu, jako je běžné, že **OK** nebo **zrušit** tlačítka, nastavte **velikosti typu** k  **Žádný**a nastavte **přesunutí typu** k **obě**. Pro **přesun X** a **přesun Y** hodnoty v rámci **přesunutí typu**, nastavit 100 % na ovládací prvek, aby zůstanou pevné vzdálenost od nejnižší pravém rohu.

     ![Dynamické rozložení](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")

4. Předpokládejme, že máte také ovládací prvek, který chcete rozšířit jako rozbalí dialogového okna. Obvykle uživatel může rozbalit dialogové okno aby bylo možné rozšířit víceřádkové textové pole zvýšit velikost textového pole, nebo se může rozšířit ovládací prvek seznamu zobrazíte další data. V takovém případě nastavte **typ velikosti** na obě a nastavte **přesunutí typu** na hodnotu none. Potom nastavte **velikosti X** a **velikosti Y** hodnoty 100.

     ![Dynamické rozložení nastavení](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")

5. Můžete experimentovat s jiné hodnoty, které může mít smysl pro vaše ovládací prvky. Dialogové okno s jednořádkové textové pole může mít **typ velikosti** nastavena na **vodorovné** jenom pro příklad.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Nastavení vlastností dynamických rozložení prostřednictvím kódu programu

Z předchozího postupu je užitečné pro určení dynamické rozložení vlastností pro dialogové okno v době návrhu, ale pokud chcete řídit dynamické rozložení za běhu, můžete nastavit vlastnosti dynamické rozložení prostřednictvím kódu programu.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Chcete-li nastavit vlastnosti dynamického rozložení prostřednictvím kódu programu

1. Vyhledat nebo vytvořit místo v kódu implementace vlastní třídy dialogového okna, ve které chcete zadat dynamické rozložení pro dialogové okno. Například můžete chtít například přidat metodu `AdjustLayout` v dialogových oken a volání z umístí where potřeba změnit rozložení. Můžete nejprve zavolat to z konstruktoru, nebo po provedení změn do dialogového okna.

2. V dialogovém okně volání [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), metoda `CWnd` třídy. `GetDynamicLayout` vrací ukazatel `CMFCDynamicLayout` objektu.

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

3. První ovládací prvek do kterého chcete přidat dynamické chování pomocí statické metody ve třídě dynamické rozložení vytvářet [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) struktura, která kóduje tak, jak ovládací prvek by měl být upraven. To provedete první volbou vhodnou statickou metodu: [CMFCDynamicLayout::MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout::MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout::MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone), nebo [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Předáte vodorovné nebo svislé aspektů přesunutí v procentech. Tyto statické metody vrátí nově vytvořený objekt MoveSettings, můžete použít k určení chování přesunutí ovládacího prvku.

   Mějte na paměti, že 100 znamená přesun přesně tak, jak dialogové okno změní velikost, která způsobí, že ovládací prvek edge zůstat pevné vzdálenost od nové ohraničení.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

4. Pro chování velikost, která používá stejnou věc udělat [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) typu. Chcete-li určit, že ovládací prvek nemění velikost přizpůsobí svou velikost dialogového okna, například pomocí následujícího kódu:

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

5. Přidejte ovládací prvek správce dynamických rozložení pomocí [CMFCDynamicLayout::AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) metody. Existují dvě přetížení pro různé způsoby určení požadované ovládacího prvku. Jeden má popisovač okna ovládacího prvku (HWND) a druhé používá ID ovládacího prvku.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

6. Opakujte pro každý ovládací prvek, který potřebuje k přesunutí nebo změně velikosti.

7. Pokud je nutné, můžete použít [CMFCDynamicLayout::HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) metodou ke zjištění, pokud ovládací prvek je již v seznamu ovládacích prvků podroben dyamic rozložení změny, nebo [CMFCDynamicLayout::IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) Metoda, která určí, jestli jsou všechny ovládací prvky, které se vztahují změny.

8. Chcete-li povolit rozložení dialogového okna, zavolejte [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) metody.

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

9. Při příštím uživatel změní velikost dialogového okna, [CMFCDynamicLayout::Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) je volána metoda, která ve skutečnosti použije nastavení.

10. Pokud chcete zakázat dynamického rozložení, zavolejte [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) s **FALSE** jako u *bEnabled* parametru.

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Programové nastavení dynamické rozložení ze souboru prostředků

1. Použití [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) metody zadejte název prostředku v souboru skriptu příslušných prostředků (soubor .rc), která určuje informace o dynamické rozložení, jako v následujícím příkladu:

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

     Pojmenovaný prostředek musí odkazovat na dialogu, který obsahuje informace o rozložení ve formě **AFX_DIALOG_LAYOUT** položku v souboru prostředků, jako v následujícím příkladu:

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>Viz také:

[CMFCDynamicLayout – třída](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[Třídy ovládacích prvků](../mfc/control-classes.md)<br/>
[Třídy dialogových oken](../mfc/dialog-box-classes.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Rozložení dynamické dialogové okno pro knihovnu MFC ve Visual C++ 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
