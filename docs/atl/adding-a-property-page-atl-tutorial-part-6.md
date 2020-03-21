---
title: Přidání stránky vlastností (ATL – tutoriál, část 6)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 467ae19c372e24b2d368002cb83367b7087136fd
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078772"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Přidání stránky vlastností (ATL – tutoriál, část 6)

> [!NOTE]
> Průvodce zprostředkovatelem OLE DB ATL není k dispozici v aplikaci Visual Studio 2019 a novější.

Stránky vlastností jsou implementovány jako samostatné objekty COM, které jim umožňují sdílet je v případě potřeby. V tomto kroku provedete následující úlohy pro přidání stránky vlastností do ovládacího prvku:

- Vytváření prostředku stránky vlastností

- Přidání kódu pro vytvoření a správu stránky vlastností

- Přidání stránky vlastností do ovládacího prvku

## <a name="creating-the-property-page-resource"></a>Vytváření prostředku stránky vlastností

Chcete-li přidat stránku vlastností k ovládacímu prvku, použijte šablonu stránky vlastností ATL.

### <a name="to-add-a-property-page"></a>Přidání stránky vlastností

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na `Polygon`.

1. V místní nabídce klikněte na **přidat** > **Nová položka**.

1. V seznamu šablon vyberte **atl** > **Stránka vlastností** ATL a klikněte na **Přidat**.

1. Jakmile se zobrazí **Průvodce stránkou vlastností ATL** , *zadejte jako* **krátký** název.

1. Kliknutím na **řetězce** otevřete stránku **řetězce** a jako **název**zadejte **& mnohoúhelník** .

   **Název** stránky vlastností je řetězec, který se zobrazí na kartě této stránky. **Řetězec doc** je popis, který rámec vlastností používá k vložení do stavového řádku nebo popisu tlačítka. Všimněte si, že standardní rámec vlastností aktuálně nepoužívá tento řetězec, takže ho můžete nechat s výchozím obsahem. V tuto chvíli nebudete generovat **soubor s nápovědě** , takže položku v tomto textovém poli odstraňte.

1. Klikněte na **Dokončit**a vytvoří se objekt stránky vlastností.

Vytvoří se následující tři soubory:

|File|Popis|
|----------|-----------------|
|PolyProp.h|Obsahuje C++ třídu `CPolyProp`, která implementuje stránku vlastností.|
|PolyProp.cpp|Zahrnuje soubor. h.|
|PolyProp.rgs|Skript registru, který registruje objekt stránky vlastností.|

Jsou také provedeny následující změny kódu:

- Nová stránka vlastností se přidá do mapování položek objektu v mnohoúhelníku. cpp.

- Třída `PolyProp` je přidána do souboru mnohoúhelník. idl.

- Nový soubor skriptu registru. rgs se přidá do prostředku projektu.

- Šablona dialogového okna je přidána do prostředku projektu pro stránku vlastností.

- Zadané řetězce vlastností jsou přidány do tabulky řetězců prostředků.

Nyní přidejte pole, která chcete zobrazit na stránce vlastností.

### <a name="to-add-fields-to-the-property-page"></a>Přidání polí na stránku vlastností

1. V **Průzkumník řešení**dvakrát klikněte na soubor prostředků mnohoúhelník. rc. Otevře se **prostředky**.

1. V **prostředky**rozbalte uzel `Dialog` a dvakrát klikněte na položku `IDD_POLYPROP`. Všimněte si, že dialogové okno, které se zobrazí, je prázdné s výjimkou popisku, který vás upozorní na vložení ovládacích prvků.

1. Vyberte tento popisek a změňte ho pro čtení `Sides:` změnou textu **titulku** v okně **vlastnosti** .

1. Změňte velikost pole popisku tak, aby odpovídala velikosti textu.

1. Přetáhněte **ovládací prvek pro úpravy** ze **sady nástrojů** na pravé straně popisku.

1. Nakonec změňte **ID** ovládacího prvku pro úpravy tak, aby `IDC_SIDES` v okně **vlastnosti** .

Tím se dokončí proces vytváření prostředku stránky vlastností.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>Přidání kódu pro vytvoření a správu stránky vlastností

Teď, když jste vytvořili prostředek stránky vlastností, musíte napsat implementační kód.

Nejprve povolte třídu `CPolyProp` pro nastavení počtu stran v objektu při stisknutí tlačítka **použít** .

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Úprava funkce použít pro nastavení počtu stran

1. Nahraďte funkci `Apply` v poli Prop. h následujícím kódem:

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

K stránce vlastností může být současně připojen více klientů, takže funkce `Apply` cyklicky přeskočí a zavolá `put_Sides` na každém klientovi s hodnotou načtenou z pole pro úpravy. Používáte třídu [CComQIPtr](../atl/reference/ccomqiptr-class.md) , která provádí `QueryInterface` na každém objektu pro získání rozhraní `IPolyCtl` z rozhraní `IUnknown` (uloženého v poli `m_ppUnk`).

Kód nyní kontroluje, zda nastavení vlastnosti `Sides` skutečně fungovalo. Pokud dojde k chybě, kód zobrazí okno se zprávou, které zobrazuje podrobnosti o chybě z rozhraní `IErrorInfo`. Kontejner obvykle vyžaduje objekt pro `ISupportErrorInfo` rozhraní a volání `InterfaceSupportsErrorInfo` nejprve, aby bylo možné určit, zda objekt podporuje nastavení informací o chybě. Tuto úlohu můžete přeskočit.

[CComPtr](../atl/reference/ccomptr-class.md) pomáhá automaticky zpracovávat počítání odkazů, takže nemusíte na rozhraní volat `Release`. `CComBSTR` pomáhá se zpracováním BSTR, takže není nutné provádět konečné `SysFreeString` volání. Použijete také jednu z různých tříd pro převod řetězce, takže v případě potřeby můžete převádět BSTR (to je důvod, proč je makro USES_CONVERSION na začátku funkce).

Také je nutné nastavit příznak nezměněného prvku stránky vlastností tak, aby označoval, že by mělo být povoleno tlačítko **použít** . K tomu dojde, když uživatel změní hodnotu v poli pro úpravy **stran** .

### <a name="to-handle-the-apply-button"></a>Postup pro zpracování tlačítka použít

1. V **zobrazení tříd**klikněte pravým tlačítkem myši na `CPolyProp` a v místní nabídce klikněte na **vlastnosti** .

1. V okně **vlastnosti** klikněte na ikonu **události** .

1. Rozbalte uzel `IDC_SIDES` v seznamu událostí.

1. Vyberte `EN_CHANGE`a v rozevírací nabídce napravo klikněte na **\<přidat > OnEnChangeSides**. Deklarace obslužné rutiny `OnEnChangeSides` bude přidána do rutiny. h a implementace obslužné rutiny do vlastností. cpp.

Dále upravíte obslužnou rutinu.

### <a name="to-modify-the-onenchangesides-method"></a>Postup úpravy metody OnEnChangeSides

1. Do metody `OnEnChangeSides` přidejte následující kód v metodě Prop. cpp (odstraněním kódu, který průvodce uvedl):

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` bude volána při odeslání zprávy `WM_COMMAND` pomocí oznámení `EN_CHANGE` pro ovládací prvek `IDC_SIDES`. `OnEnChangeSides` pak zavolá `SetDirty` a předá hodnotu TRUE, aby označovala, že stránka vlastností je nyní nečistá a mělo by být povoleno tlačítko **použít** .

## <a name="adding-the-property-page-to-the-control"></a>Přidání stránky vlastností do ovládacího prvku

Šablona stránky vlastností ATL a Průvodce nepřidá stránku vlastností do ovládacího prvku automaticky, protože v projektu může být více ovládacích prvků. Bude nutné přidat položku k mapě vlastností ovládacího prvku.

### <a name="to-add-the-property-page"></a>Přidání stránky vlastností

1. Otevřete PolyCtl. h a přidejte tyto řádky do mapy vlastností:

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

Mapa vlastností ovládacího prvku teď vypadá takto:

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

Mohli jste přidat `PROP_PAGE` makro s identifikátorem CLSID stránky vlastností, ale pokud použijete makro `PROP_ENTRY`, jak je zobrazeno, hodnota vlastnosti `Sides` je také uložena při uložení ovládacího prvku.

Tři parametry makra jsou popis vlastnosti, identifikátor DISPID vlastnosti a identifikátor CLSID stránky vlastností, která na něm má vlastnost. To je užitečné, pokud například nanačítáte ovládací prvek do Visual Basic a nastavíte počet stran v době návrhu. Vzhledem k tomu, že se počet stran ukládá, při opětovném načtení Visual Basic projektu se obnoví počet stran.

## <a name="building-and-testing-the-control"></a>Sestavování a testování ovládacího prvku

Nyní Sestavte tento ovládací prvek a vložte ho do kontejneru testů ovládacího prvku ActiveX. V části **kontejner testů**v nabídce **Úpravy** klikněte na **objekt třídy PolyCtl**. Zobrazí se stránka vlastností s informacemi, které jste přidali.

Tlačítko **použít** je zpočátku zakázané. Začněte psát hodnotu do pole **strany** a aktivuje se tlačítko **použít** . Až dokončíte zadávání hodnoty, klikněte na tlačítko **použít** . Ovládací prvek zobrazuje změny a tlačítko **použít** je opět zakázané. Zkuste zadat neplatnou hodnotu. Zobrazí se okno se zprávou obsahující popis chyby, který jste nastavili ve funkci `put_Sides`.

Dále umístíte ovládací prvek na webovou stránku.

[Zpátky ke kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [na krok 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)
