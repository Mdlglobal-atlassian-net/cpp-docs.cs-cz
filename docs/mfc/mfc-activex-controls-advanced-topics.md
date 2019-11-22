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
ms.openlocfilehash: 9f1fa862a30a83cbda049fc63bac6c33a101587b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305382"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC – ovládací prvky ActiveX: Pokročilá témata

Tento článek se věnuje pokročilým tématům, která souvisí s vývojem ovládacích prvků ActiveX. Mezi ně patří:

- [Použití databázových tříd v ovládacích prvcích ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementace parametrizované vlastnosti](#_core_implementing_a_parameterized_property)

- [Zpracování chyb v ovládacím prvku ActiveX](#_core_handling_errors_in_your_activex_control)

- [Zpracování speciálních klíčů v ovládacím prvku](#_core_handling_special_keys_in_your_control)

- [Přístup k ovládacím prvkům dialogových oken, které jsou v době běhu neviditelné](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX je starší verze technologie, která by se neměla používat pro nový vývoj. Další informace o moderních technologiích, které nahrazují prvky ActiveX, naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a>Použití databázových tříd v ovládacích prvcích ActiveX

Vzhledem k tomu, že třídy ovládacích prvků ActiveX jsou součástí knihovny tříd, lze použít stejné postupy a pravidla pro použití databázových tříd v standardní aplikaci knihovny MFC pro vývoj ovládacích prvků ActiveX, které používají databázové třídy knihovny MFC.

Obecný přehled databázových tříd knihovny MFC naleznete v tématu [třídy databáze MFC (rozhraní DAO a rozhraní ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Článek zavádí jak třídy knihovny MFC rozhraní ODBC, tak třídy MFC DAO a směruje vás na další podrobnosti.

> [!NOTE]
> Rozhraní DAO je podporováno prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou. Vizuální C++ prostředí a Průvodci nepodporují rozhraní DAO (i když třídy rozhraní DAO jsou zahrnuty a je možné je nadále používat). Společnost Microsoft doporučuje, abyste pro nové projekty používali [šablony OLE DB](../data/oledb/ole-db-programming.md) nebo [rozhraní ODBC a knihovnu MFC](../data/odbc/odbc-and-mfc.md) . V údržbě stávajících aplikací byste měli používat jenom rozhraní DAO.

##  <a name="_core_implementing_a_parameterized_property"></a>Implementace parametrizované vlastnosti

Parametrizovaná vlastnost (někdy označovaná jako pole vlastností) je metoda pro vystavení homogenní kolekce hodnot jako jediná vlastnost ovládacího prvku. Můžete například použít parametrizovanou vlastnost k vystavení pole nebo slovníku jako vlastnost. V Visual Basic je k této vlastnosti přistupovaná pomocí notace Array:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Použijte Průvodce přidáním vlastnosti k implementaci parametrizované vlastnosti. Průvodce přidáním vlastnosti implementuje vlastnost přidáním páru funkcí get/set, které umožňují uživateli ovládacího prvku získat přístup k vlastnosti pomocí výše uvedeného zápisu nebo standardního způsobu.

Podobně jako metody a vlastnosti jsou parametrizované vlastnosti také omezeny na počet povolených parametrů. V případě parametrizovaných vlastností je limit 15 parametrů (s jedním parametrem vyhrazeným pro uložení hodnoty vlastnosti).

Následující postup přidá parametrizovanou vlastnost nazvanou Array, ke které lze přistupovat jako dvojrozměrné pole celých čísel.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Přidání parametrizované vlastnosti pomocí Průvodce přidáním vlastnosti

1. Načtěte projekt ovládacího prvku.

1. V Zobrazení tříd rozbalte uzel Knihovna vašeho ovládacího prvku.

1. Klikněte pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) a otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom klikněte na **Přidat vlastnost**.

1. Do pole **název vlastnosti** zadejte `Array`.

1. V poli **typ vlastnosti** vyberte možnost **krátký**.

1. V případě typu **implementace** klikněte na tlačítko **získat nebo nastavit metody**.

1. Do polí **získat** a **nastavit funkce** zadejte jedinečné názvy pro funkce Get a set nebo přijměte výchozí názvy.

9. Přidejte parametr s názvem *řádek* (typ *short*) pomocí ovládacích prvků **název parametru** a **typ parametru** .

10. Přidejte druhý parametr nazvaný *Column* (typ *short*).

11. Klikněte na tlačítko **Dokončit**.

### <a name="changes-made-by-the-add-property-wizard"></a>Změny provedené Průvodcem přidáním vlastnosti

Když přidáte vlastní vlastnost, Průvodce přidáním vlastnosti provede změny v záhlaví třídy ovládacího prvku (. H) a implementace (. CPP) soubory.

Následující řádky jsou přidány do třídy ovládacího prvku. Soubor H:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Tento kód deklaruje dvě funkce nazvané `GetArray` a `SetArray`, které umožňují uživateli při přístupu k vlastnosti požádat o konkrétní řádek a sloupec.

Kromě toho Průvodce přidáním vlastnosti přidá následující řádky do mapy odeslání ovládacího prvku umístěnou v implementaci třídy ovládacího prvku (. CPP):

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Nakonec jsou do konce okna přidány implementace funkcí `GetArray` a `SetArray`. Soubor CPP. Ve většině případů upravíte funkci get tak, aby vracela hodnotu vlastnosti. Funkce Set obvykle obsahuje kód, který by se měl spustit, buď před nebo po změně vlastnosti.

Aby byla tato vlastnost užitečná, mohli byste deklarovat proměnnou člena dvourozměrného pole ve třídě ovládacího prvku typu **short**pro ukládání hodnot pro parametrizovanou vlastnost. Pak můžete změnit funkci get tak, aby vracela hodnotu uloženou ve správném řádku a sloupci, jak je uvedeno v parametrech, a upravit funkci set tak, aby aktualizovala hodnotu, na kterou odkazuje parametr řádku a sloupce.

##  <a name="_core_handling_errors_in_your_activex_control"></a>Zpracování chyb v ovládacím prvku ActiveX

Pokud dojde k chybovým podmínkám v ovládacím prvku, může být nutné ohlásit chybu do kontejneru ovládacích prvků. Existují dvě metody pro hlášení chyb v závislosti na situaci, ve které dojde k chybě. Pokud k chybě dojde v rámci funkce Get nebo set vlastnosti nebo v rámci implementace metody automatizace OLE, ovládací prvek by měl zavolat [COleControl –:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror), který signalizuje uživateli ovládacího prvku, že došlo k chybě. Pokud k chybě dojde v jinou dobu, ovládací prvek by měl zavolat [COleControl –:: FireError –](../mfc/reference/colecontrol-class.md#fireerror), což vyvolá chybovou událost typu akcie.

Chcete-li určit druh chyby, ke které došlo, ovládací prvek musí předat kód chyby `ThrowError` nebo `FireError`. Kód chyby je stavový kód OLE, který má 32ovou hodnotu. Pokud je to možné, vyberte kód chyby ze standardní sady kódů definovaných v OLECTL. Soubor hlaviček H Následující tabulka shrnuje tyto kódy.

### <a name="activex-control-error-codes"></a>Kódy chyb ovládacích prvků ActiveX

|Chyba|Popis|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Neplatné volání funkce|
|CTL_E_OVERFLOW|Plně|
|CTL_E_OUTOFMEMORY|Nedostatek paměti|
|CTL_E_DIVISIONBYZERO|Dělení nulou|
|CTL_E_OUTOFSTRINGSPACE|Nedostatek místa pro řetězec|
|CTL_E_OUTOFSTACKSPACE|Nedostatek místa v zásobníku|
|CTL_E_BADFILENAMEORNUMBER|Chybný název souboru nebo číslo|
|CTL_E_FILENOTFOUND|Soubor se nenašel.|
|CTL_E_BADFILEMODE|Chybný režim souboru|
|CTL_E_FILEALREADYOPEN|Soubor již je otevřen.|
|CTL_E_DEVICEIOERROR|Vstupně-výstupní chyba zařízení|
|CTL_E_FILEALREADYEXISTS|Soubor už existuje.|
|CTL_E_BADRECORDLENGTH|Chybná délka záznamu|
|CTL_E_DISKFULL|Plný disk|
|CTL_E_BADRECORDNUMBER|Chybné číslo záznamu|
|CTL_E_BADFILENAME|Chybný název souboru|
|CTL_E_TOOMANYFILES|Příliš mnoho souborů|
|CTL_E_DEVICEUNAVAILABLE|Nedostupné zařízení|
|CTL_E_PERMISSIONDENIED|Oprávnění byla odepřena.|
|CTL_E_DISKNOTREADY|Disk není připravený|
|CTL_E_PATHFILEACCESSERROR|Chyba přístupu k cestě nebo k souboru|
|CTL_E_PATHNOTFOUND|Cesta nebyla nalezena.|
|CTL_E_INVALIDPATTERNSTRING|Neplatný řetězec vzoru|
|CTL_E_INVALIDUSEOFNULL|Neplatné použití hodnoty NULL|
|CTL_E_INVALIDFILEFORMAT|Neplatný formát souboru|
|CTL_E_INVALIDPROPERTYVALUE|Neplatná hodnota vlastnosti|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Neplatný index pole vlastností|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Sada není podporována v době běhu.|
|CTL_E_SETNOTSUPPORTED|Sada není podporovaná (vlastnost jen pro čtení)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Je vyžadován index pole vlastností.|
|CTL_E_SETNOTPERMITTED|Sada není povolená.|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|V době běhu není podporováno načítání|
|CTL_E_GETNOTSUPPORTED|Vlastnost get není podporována (vlastnost pouze pro zápis).|
|CTL_E_PROPERTYNOTFOUND|Vlastnost nebyla nalezena.|
|CTL_E_INVALIDCLIPBOARDFORMAT|Neplatný formát schránky|
|CTL_E_INVALIDPICTURE|Neplatný obrázek|
|CTL_E_PRINTERERROR|Chyba tiskárny|
|CTL_E_CANTSAVEFILETOTEMP|Soubor nelze uložit do DOČASNÉho souboru.|
|CTL_E_SEARCHTEXTNOTFOUND|Hledaný text nebyl nalezen.|
|CTL_E_REPLACEMENTSTOOLONG|Příliš dlouhé náhrady|

V případě potřeby použijte makro CUSTOM_CTL_SCODE k definování vlastního kódu chyby pro podmínku, která není pokrytá jedním ze standardních kódů. Parametr pro toto makro by měl být celé číslo v rozmezí od 1000 do 32767 (včetně). Příklad:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Pokud vytváříte ovládací prvek ActiveX, který nahradí existující ovládací prvek VBX, definujte kódy chyb ovládacích prvků ActiveX se stejnými číselnými hodnotami, které ovládací prvek VBX používá k zajištění kompatibility kódů chyb.

##  <a name="_core_handling_special_keys_in_your_control"></a>Zpracování speciálních klíčů v ovládacím prvku

V některých případech můžete chtít speciální kombinace klávesových zkratek zpracovat zvláštním způsobem; Například vložte nový řádek při stisknutí klávesy ENTER v ovládacím prvku víceřádkový textový rámeček nebo při stisknutí ID směrového klíče mezi skupinu ovládacích prvků pro úpravy.

Pokud je základní třída ovládacího prvku ActiveX `COleControl`, můžete přepsat [CWnd::P retranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage) ke zpracování zpráv předtím, než je kontejner zpracuje. Při použití této techniky vždy vrátí **hodnotu true** , pokud zprávu zpracováváte v přepsání `PreTranslateMessage`.

Následující příklad kódu ukazuje možný způsob zpracování všech zpráv souvisejících se směrovým klíčem.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Další informace o manipulaci s rozhraními klávesnice pro ovládací prvek ActiveX naleznete v dokumentaci sady ActiveX SDK.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Přístup k ovládacím prvkům dialogových oken, které jsou v době běhu neviditelné

Můžete vytvořit ovládací prvky dialogu, které nemají žádné uživatelské rozhraní a jsou v době běhu neviditelné. Pokud přidáte neviditelný ovládací prvek ActiveX v době spuštění do dialogového okna a použijete [CWnd:: GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pro přístup k ovládacímu prvku, ovládací prvek nebude pracovat správně. Místo toho byste měli použít jeden z následujících postupů pro získání objektu, který představuje ovládací prvek:

- Pomocí Průvodce přidáním členské proměnné vyberte **řídicí proměnnou** a potom vyberte ID ovládacího prvku. Zadejte název členské proměnné a jako **typ ovládacího prvku**vyberte obálkovou třídu ovládacího prvku.

     -nebo-

- Deklaruje místní proměnnou a podtřídu jako položku dialogového okna. Vložte kód, který se podobá následujícímu (`CMyCtrl` je Obálková třída, IDC_MYCTRL1 je ID ovládacího prvku):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
