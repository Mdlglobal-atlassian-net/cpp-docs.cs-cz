---
title: 'MFC – ovládací prvky ActiveX: Pokročilá témata'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364630"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC – ovládací prvky ActiveX: Pokročilá témata

Tento článek popisuje pokročilá témata související s vývojem ovládacích prvků ActiveX. Mezi ně patří:

- [Použití tříd databáze v ovládacích prvcích ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementace parametrizované vlastnosti](#_core_implementing_a_parameterized_property)

- [Zpracování chyb v ovládacím prvku ActiveX](#_core_handling_errors_in_your_activex_control)

- [Manipulace se speciálními klávesami v ovládacím prvku](#_core_handling_special_keys_in_your_control)

- [Přístup k ovládacím prvkům dialogu, které jsou za běhu neviditelné](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>Použití tříd databáze v ovládacích prvcích ActiveX

Vzhledem k tomu, že třídy ovládacího prvku ActiveX jsou součástí knihovny tříd, můžete použít stejné postupy a pravidla pro použití tříd databáze ve standardní aplikaci knihovny MFC k vývoji ovládacích prvků ActiveX, které používají třídy databáze knihovny MFC.

Obecný přehled tříd databáze knihovny MFC naleznete v [tématu Třídy databáze knihovny MFC (DAO a ODBC).](../data/mfc-database-classes-odbc-and-dao.md) Článek zavádí třídy MFC ODBC a třídy Knihovny MFC DAO a přesměruje vás na další podrobnosti o obou.

> [!NOTE]
> DAO je podporováno prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé. Prostředí Visual C++ a průvodci nepodporují DAO (i když jsou zahrnuty třídy DAO a můžete je stále používat). Společnost Microsoft doporučuje používat [šablony OLE DB](../data/oledb/ole-db-programming.md) nebo rozhraní [ODBC a knihovnu MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat pouze při údržbě existujících aplikací.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>Implementace parametrizované vlastnosti

Parametrizovaná vlastnost (někdy volaná pole vlastností) je metoda pro vystavení homogenní kolekce hodnot jako jediné vlastnosti ovládacího prvku. Například můžete použít parametrizovanou vlastnost k vystavení pole nebo slovníku jako vlastnosti. V jazyce Visual Basic je tato vlastnost přístupná pomocí zápisu pole:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Pomocí Průvodce přidáním vlastností implementujte parametrizovanou vlastnost. Průvodce přidáním vlastnosti implementuje vlastnost přidáním dvojice funkcí Get/Set, které umožňují uživateli ovládacího prvku přístup k vlastnosti pomocí výše uvedeného zápisu nebo standardním způsobem.

Podobně jako metody a vlastnosti, parametrizované vlastnosti mají také limit na počet povolených parametrů. V případě parametrizovaných vlastností je limit 15 parametrů (s jedním parametrem vyhrazeným pro uložení hodnoty vlastnosti).

Následující postup přidá parametrizovanou vlastnost nazvanou Array, ke které lze přistupovat jako k dvojrozměrnému poli celočísel.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Přidání parametrizované vlastnosti pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

1. Do pole **Název vlastnosti** zadejte . `Array`

1. V poli **Typ vlastnosti** vyberte **krátký**.

1. V **souboru Typ implementace** klepněte na tlačítko Získat nebo nastavit **metody**.

1. Do polí **Získat funkci** a **Nastavit funkci** zadejte jedinečné názvy funkcí Get a Set nebo přijměte výchozí názvy.

1. Přidejte parametr, nazývaný *řádek* (typ *krátký*), pomocí ovládacích prvků **Název parametru** a **Typ parametru.**

1. Přidejte druhý parametr nazývaný *sloupec* (zadejte *krátký).*

1. Klikněte na **Finish** (Dokončit).

### <a name="changes-made-by-the-add-property-wizard"></a>Změny provedené Průvodcem přidáním vlastností

Když přidáte vlastní vlastnost, Průvodce přidáním vlastností provede změny v záhlaví třídy ovládacího prvku (. H) a provádění (. CPP).

Následující řádky jsou přidány do třídy ovládacího prvku . H soubor:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Tento kód deklaruje dvě volané `GetArray` funkce, `SetArray` které umožňují uživateli požádat o určitý řádek a sloupec při přístupu k vlastnosti.

Průvodce přidáním vlastnosti navíc přidá následující řádky do mapy dispečera dispečinku ovládacího prvku, která se nachází v implementaci třídy řízení (. CPP) soubor:

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Nakonec jsou implementace `GetArray` funkcí `SetArray` a přidány na konec . CPP. Ve většině případů upravíte Get funkce vrátit hodnotu vlastnosti. Funkce Set bude obvykle obsahovat kód, který by měl být spuštěn před nebo po změně vlastnosti.

Aby byla tato vlastnost užitečná, můžete deklarovat dvourozměrnou členovou proměnnou pole ve třídě ovládacího prvku typu **short**, pro uložení hodnot pro parametrizovanou vlastnost. Potom můžete upravit Get funkce vrátit hodnotu uloženou na správný řádek a sloupec, jak je uvedeno parametry a upravit Set funkce aktualizovat hodnotu odkazuje řádek a sloupec parametry.

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>Zpracování chyb v ovládacím prvku ActiveX

Pokud dojde k chybám v ovládacím prvku, bude pravděpodobně nutné ohlásit chybu do kontejneru ovládacího prvku. Existují dvě metody pro hlášení chyb, v závislosti na situaci, ve které dojde k chybě. Pokud dojde k chybě v rámci funkce Get nebo Set vlastnosti nebo v rámci implementace metody OLE Automation, ovládací prvek by měl volat [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), který signalizuje uživateli ovládacího prvku, že došlo k chybě. Pokud k chybě dojde kdykoli jindy, ovládací prvek by měl volat [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), který vyvolá událost Stock Error.

Chcete-li označit druh chyby, ke které došlo, `ThrowError` `FireError`musí ovládací prvek předat kód chyby nebo . Kód chyby je stavový kód OLE, který má 32bitovou hodnotu. Pokud je to možné, zvolte kód chyby ze standardní sady kódů definovaných v OLECTL. H hlavičkový soubor. Následující tabulka shrnuje tyto kódy.

### <a name="activex-control-error-codes"></a>Kódy chyb ovládacího prvku ActiveX

|Chyba|Popis|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Volání neplatných funkcí|
|CTL_E_OVERFLOW|Přetečení|
|CTL_E_OUTOFMEMORY|Nedostatek paměti|
|CTL_E_DIVISIONBYZERO|Dělení nulou|
|CTL_E_OUTOFSTRINGSPACE|Nedostatek místa pro řetězec|
|CTL_E_OUTOFSTACKSPACE|Nedostatek místa v zásobníku|
|CTL_E_BADFILENAMEORNUMBER|Chybný název souboru nebo číslo|
|CTL_E_FILENOTFOUND|Soubor nebyl nalezen.|
|CTL_E_BADFILEMODE|Chybný režim souboru|
|CTL_E_FILEALREADYOPEN|Soubor již je otevřen.|
|CTL_E_DEVICEIOERROR|Vstupně-výstupní chyba zařízení|
|CTL_E_FILEALREADYEXISTS|Soubor již existuje.|
|CTL_E_BADRECORDLENGTH|Chybná délka záznamu|
|CTL_E_DISKFULL|Disk plný|
|CTL_E_BADRECORDNUMBER|Chybné číslo záznamu|
|CTL_E_BADFILENAME|Chybný název souboru|
|CTL_E_TOOMANYFILES|Příliš mnoho souborů|
|CTL_E_DEVICEUNAVAILABLE|Zařízení není k dispozici.|
|CTL_E_PERMISSIONDENIED|Oprávnění se zamítlo|
|CTL_E_DISKNOTREADY|Disk není připraven|
|CTL_E_PATHFILEACCESSERROR|Chyba přístupu cesty/souboru|
|CTL_E_PATHNOTFOUND|Cesta nebyla nalezena.|
|CTL_E_INVALIDPATTERNSTRING|Neplatný řetězec vzorku|
|CTL_E_INVALIDUSEOFNULL|Neplatné použití null|
|CTL_E_INVALIDFILEFORMAT|Neplatný formát souboru|
|CTL_E_INVALIDPROPERTYVALUE|Neplatná hodnota vlastnosti|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Neplatný index pole vlastností|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Nastavit není podporováno za běhu|
|CTL_E_SETNOTSUPPORTED|Sada není podporována (vlastnost jen pro čtení)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Je vyžadován index pole vlastností.|
|CTL_E_SETNOTPERMITTED|Nastaveno není povoleno.|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Nepodporovat za běhu|
|CTL_E_GETNOTSUPPORTED|Nepodporované (vlastnost pouze pro zápis)|
|CTL_E_PROPERTYNOTFOUND|Vlastnost nebyla nalezena.|
|CTL_E_INVALIDCLIPBOARDFORMAT|Neplatný formát schránky|
|CTL_E_INVALIDPICTURE|Neplatný obrázek|
|CTL_E_PRINTERERROR|Chyba tiskárny|
|CTL_E_CANTSAVEFILETOTEMP|Nelze uložit soubor do TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|Hledaný text nebyl nalezen.|
|CTL_E_REPLACEMENTSTOOLONG|Náhradní díly jsou příliš dlouhé|

V případě potřeby použijte CUSTOM_CTL_SCODE makro k definování vlastního kódu chyby pro podmínku, která není pokryta jedním ze standardních kódů. Parametr pro toto makro by měl být celé číslo mezi 1000 a 32767 včetně. Příklad:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Pokud vytváříte ovládací prvek ActiveX, který nahradí existující ovládací prvek VBX, definujte kódy chyb ovládacího prvku ActiveX stejnými číselnými hodnotami, které ovládací prvek VBX používá k zajištění kompatibility kódů chyb.

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>Manipulace se speciálními klávesami v ovládacím prvku

V některých případech můžete chtít zpracovat určité kombinace kláves zvláštním způsobem; vložte například nový řádek, když je klávesa ENTER stisknuta v ovládacím prvku víceřádkového textového pole nebo se při stisknutí ID směrové klávesy přesune mezi skupinou ovládacích prvků pro úpravy.

Pokud je `COleControl`základní třída ovládacího prvku ActiveX , můžete přepsat [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) pro zpracování zpráv před kontejner uvládne. Při použití této techniky, vždy vrátit **TRUE,** pokud `PreTranslateMessage`zpracováváte zprávu v přepsání .

Následující příklad kódu ukazuje možný způsob zpracování všech zpráv souvisejících se směrové klíče.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Další informace o zpracování rozhraní klávesnice pro ovládací prvek ActiveX naleznete v dokumentaci k sada ActiveX SDK.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Přístup k ovládacím prvkům dialogových oken, které jsou za běhu neviditelné

Můžete vytvořit ovládací prvky dialogového okna, které nemají žádné uživatelské rozhraní a jsou neviditelné za běhu. Pokud přidáte neviditelný za běhu ovládací prvek ActiveX do dialogového okna a pomocí [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pro přístup k ovládacímu prvku, ovládací prvek nebude fungovat správně. Místo toho byste měli použít jednu z následujících technik k získání objektu, který představuje ovládací prvek:

- Pomocí Průvodce přidáním členské proměnné vyberte **Možnost řízení a** pak vyberte ID ovládacího prvku. Zadejte název členské proměnné a vyberte třídu obálky ovládacího prvku jako **typ ovládacího prvku**.

     -nebo-

- Deklarujte jako položku dialogu místní proměnnou a podtřídu. Vložte kód, který`CMyCtrl` se podobá následující ( je obálka třídy, IDC_MYCTRL1 je ID ovládacího prvku):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
