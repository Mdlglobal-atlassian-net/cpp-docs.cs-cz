---
title: 'MFC – ovládací prvky ActiveX: Pokročilá témata | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18d0a15b2fe1d61e1b7ba14d210b428f282bff4d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386363"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC – ovládací prvky ActiveX: Pokročilá témata

Tento článek se týká Pokročilá témata související s vývojem ovládací prvky ActiveX. Zde jsou některé z nich:

- [Použití databázových tříd v ovládacích prvcích ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementace Parametrizovaná vlastnost](#_core_implementing_a_parameterized_property)

- [Zpracování chyb v ovládacím prvku ActiveX](#_core_handling_errors_in_your_activex_control)

- [Speciální klávesy zpracování v ovládacím prvku](#_core_handling_special_keys_in_your_control)

- [Přístup k ovládacím prvkům dialogové okno, které nejsou viditelná v době běhu](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a> Použití databázových tříd v ovládacích prvcích ActiveX

Protože třídy ovládacích prvků ActiveX jsou součástí knihovny tříd, můžete použít stejné postupy a pravidla pro použití databázových tříd ve standardní aplikace knihovny MFC k vývoji ovládacích prvků ActiveX, které používají databázové třídy MFC.

Obecný přehled o databázových tříd MFC, naleznete v tématu [MFC – databázové třídy (rozhraní DAO a ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Tento článek představuje třídy MFC rozhraní ODBC a DAO knihovny MFC, třídy a vás přesměruje na další podrobnosti o buď.

> [!NOTE]
>  Prostředí Visual C++ a Průvodce nepodporuje rozhraní DAO (i když jsou součástí třídy DAO a můžete stále použít). Microsoft doporučuje, abyste použili [šablony technologie OLE DB](../data/oledb/ole-db-programming.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom v udržování existujících aplikací.

##  <a name="_core_implementing_a_parameterized_property"></a> Implementace Parametrizovaná vlastnost

Parametrizovaná vlastnost (říká se jim vlastnost pole) je metoda vystavení homogenní kolekci hodnot jako jednu vlastnost ovládacího prvku. Můžete například použít Parametrizovaná vlastnost vystavit pole nebo slovníku jako vlastnost. V jazyce Visual Basic je tato vlastnost přistupovat pomocí zápisu pole:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Pomocí Průvodce přidáním vlastnosti do implementace parametrizované vlastnosti. Průvodce přidáním vlastnosti implementuje vlastnost přidáním páru Get/Set funkcí, které umožňují uživateli přístup k vlastnosti pomocí výše uvedeného zápisu nebo standardním způsobem.

Podobá se vlastnosti parametrizované vlastnosti a metody mají také omezený počet povolených parametrů. V případě parametrizované vlastnosti limit je 15 parametry (s jedním parametrem vyhrazeno pro uložení hodnoty vlastnosti).

Následující procedura přidá parametrizovanou vlastnost s názvem pole, které mohou být přístupné jako dvourozměrné pole celých čísel.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Chcete-li přidat parametrizované vlastnosti pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

1. V **název vlastnosti** zadejte `Array`.

1. V **typ vlastnosti** vyberte **krátký**.

1. Pro **implementace** typu, klikněte na tlačítko **metody Get/Set**.

1. V **získat funkce** a **nastavení funkce** polí, zadejte jedinečné názvy pro získání a nastavení funkce nebo přijměte výchozí názvy.

9. Přidat parametr s názvem *řádek* (typ *krátký*), použije **název parametru** a **typ parametru** ovládacích prvků.

10. Přidejte druhý parametr s názvem *sloupec* (typ *krátký*).

11. Klikněte na tlačítko **Dokončit**.

### <a name="changes-made-by-the-add-property-wizard"></a>Změny provedené Průvodce přidáním vlastnosti

Když přidáte vlastní vlastnost, Průvodce přidáním vlastnosti změní záhlaví třídy ovládacího prvku (. H) a implementace (. Soubory CPP).

Následující řádky se přidají do třídy ovládacího prvku. H souboru:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Tento kód deklaruje dvě funkce volané `GetArray` a `SetArray` , která umožňují uživateli požadovat konkrétní řádek a sloupec při přístupu k vlastnosti.

Kromě toho Průvodce přidáním vlastnosti přidá následující řádky do mapa odeslání ovládací prvek, který je umístěný v implementaci třídy ovládacího prvku (. Soubor CPP):

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Nakonec implementace `GetArray` a `SetArray` funkce jsou přidány na konec objektu. Soubor CPP. Ve většině případů se upravit funkci Get vrátit hodnotu vlastnosti. Funkci Set bude obvykle obsahovat kód, který by měl být spuštěn, před nebo po změně vlastnosti.

Pro tuto vlastnost na vhodné, můžete deklarovat členské proměnné dvourozměrné pole ve třídě ovládacího prvku typu **krátký**pro uložení hodnoty parametrizované vlastnosti. Může upravit funkci Get vrátit hodnotu uloženou v správné řádků a sloupců, jak je uvedeno parametry a upravte funkci Set k aktualizaci hodnoty odkazuje parametry řádků a sloupců.

##  <a name="_core_handling_errors_in_your_activex_control"></a> Zpracování chyb v ovládacím prvku ActiveX

Pokud dojde k chybové stavy v ovládacím prvku, budete muset ohlaste chybu kontejneru ovládacího prvku. Existují dvě metody pro hlášení chyb, v závislosti na situaci, ve kterém dojde k chybě. Pokud dojde k chybě v rámci vlastnosti získání nebo nastavení funkce, nebo v rámci implementace metody automatizace OLE, by měly volat ovládací prvek [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), které signály uživateli ovládacího prvku, který došlo k chybě. Pokud dojde k chybě v každém okamžiku, by měly volat ovládací prvek [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), která aktivuje základní událost chyby.

Označuje typ chyby, ke kterým došlo, ovládací prvek musí projít chybový kód k `ThrowError` nebo `FireError`. Kód chyby je stavový kód OLE, který má hodnotu 32-bit. Pokud je to možné, zvolte z standardní sadu kódy definované v OLECTL chybový kód. Soubor hlaviček H. Následující tabulka shrnuje tyto kódy.

### <a name="activex-control-error-codes"></a>Chybové kódy ovládacího prvku ActiveX

|Chyba|Popis|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Neplatné volání funkce|
|CTL_E_OVERFLOW|přetečení|
|CTL_E_OUTOFMEMORY|Nedostatek paměti|
|CTL_E_DIVISIONBYZERO|Dělení nulou|
|CTL_E_OUTOFSTRINGSPACE|Nedostatek místa pro řetězce|
|CTL_E_OUTOFSTACKSPACE|Nedostatek místa v zásobníku|
|CTL_E_BADFILENAMEORNUMBER|Chybný název souboru nebo číslo|
|CTL_E_FILENOTFOUND|Soubor nebyl nalezen|
|CTL_E_BADFILEMODE|Chybný režim souboru|
|CTL_E_FILEALREADYOPEN|Soubor již je otevřen.|
|CTL_E_DEVICEIOERROR|Vstupně-výstupní chyba zařízení|
|CTL_E_FILEALREADYEXISTS|Soubor již existuje.|
|CTL_E_BADRECORDLENGTH|Chybná délka záznamu|
|CTL_E_DISKFULL|Disk je plný|
|CTL_E_BADRECORDNUMBER|Chybné číslo záznamu|
|CTL_E_BADFILENAME|Chybný název souboru|
|CTL_E_TOOMANYFILES|Příliš mnoho souborů|
|CTL_E_DEVICEUNAVAILABLE|Zařízení není k dispozici|
|CTL_E_PERMISSIONDENIED|Oprávnění byla odepřena.|
|CTL_E_DISKNOTREADY|Disk není připraven|
|CTL_E_PATHFILEACCESSERROR|Chyba přístupu k cestě nebo k souboru|
|CTL_E_PATHNOTFOUND|Cesta nebyla nalezena.|
|CTL_E_INVALIDPATTERNSTRING|Neplatný řetězec vzoru.|
|CTL_E_INVALIDUSEOFNULL|Neplatné použití hodnoty NULL|
|CTL_E_INVALIDFILEFORMAT|Neplatný formát souboru|
|CTL_E_INVALIDPROPERTYVALUE|Neplatná hodnota vlastnosti|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Neplatný index pole vlastností|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Metoda Set není podporována v době běhu|
|CTL_E_SETNOTSUPPORTED|Metoda Set není podporována (vlastnost jen pro čtení)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Je vyžadován index pole vlastností.|
|CTL_E_SETNOTPERMITTED|Metoda Set není povolena|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Metoda Get není podporována v době běhu|
|CTL_E_GETNOTSUPPORTED|Získat není podporována (vlastnost je jen pro zápis)|
|CTL_E_PROPERTYNOTFOUND|Vlastnost nebyla nalezena.|
|CTL_E_INVALIDCLIPBOARDFORMAT|Neplatný formát schránky|
|CTL_E_INVALIDPICTURE|Neplatný obrázek|
|CTL_E_PRINTERERROR|Chyba tiskárny|
|CTL_E_CANTSAVEFILETOTEMP|Soubor nelze dočasně uložit.|
|CTL_E_SEARCHTEXTNOTFOUND|Hledaný text nebyl nalezen|
|CTL_E_REPLACEMENTSTOOLONG|Příliš dlouhá nahrazení|

V případě potřeby použijte makro CUSTOM_CTL_SCODE definovat kód vlastní chybovou podmínku, která není součástí některá standardní kódy. Parametr tohoto makra by měl být celé číslo mezi 1 000 a 32767 (včetně). Příklad:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Při vytváření ovládacího prvku ActiveX k nahrazení existujícího ovládacího prvku VBX definujte ActiveX chybové kódy ovládacího prvku pomocí stejné číselné hodnoty, které ovládací prvek VBX používá k zajištění, že kódy chyb jsou kompatibilní.

##  <a name="_core_handling_special_keys_in_your_control"></a> Speciální klávesy zpracování v ovládacím prvku

V některých případech můžete chtít zpracovat určité kombinace kláves zvláštním způsobem; například ovládací prvky vložit nový řádek při stisknutí klávesy ENTER ve víceřádkovém textovém poli ovládací prvek nebo jejich sdílení mezi skupinu upravit, směrové při stisknutí ID klíče.

Pokud je základní třída ovládacího prvku ActiveX `COleControl`, můžete přepsat [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) zpracovat zprávy před jejich zpracování kontejneru. Když používáte tuto techniku, vždy vrátí **TRUE** Pokud zpracovat zprávu v přepsání metody `PreTranslateMessage`.

Následující příklad kódu ukazuje možným způsobem zpracovávat všechny zprávy týkající se směrové klíče.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Další informace o zpracování rozhraní klávesnice pro ovládací prvek ActiveX naleznete v dokumentaci k ActiveX SDK.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> Přístup k ovládacím prvkům dialogové okno, které nejsou viditelná v době běhu

Můžete vytvořit ovládací prvky dialogového okna, které jste žádné uživatelské rozhraní a nejsou viditelná v době běhu. Pokud chcete přidat skrytý v době běhu ovládacího prvku ActiveX k dialogovému oknu a použití [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pro přístup k ovládací prvek, ovládací prvek nebude fungovat správně. Místo toho používejte jeden z následujících postupů k získání objektu, který představuje ovládací prvek:

- Pomocí Průvodce přidáním členské proměnné, vyberte **proměnné ovládacího prvku** a pak vyberte ID ovládacího prvku. Zadejte název proměnné člena a vyberte třídu obálky ovládacího prvku jako **– typ ovládacího prvku**.

     -nebo-

- Deklarujte místní proměnné a podtřídy jako položky dialogového okna. Vložte kód, který má následující podobu (`CMyCtrl` je třídou obálky IDC_MYCTRL1 je ID ovládacího prvku):

     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

