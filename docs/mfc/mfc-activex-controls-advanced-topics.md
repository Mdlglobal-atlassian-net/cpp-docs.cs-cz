---
title: "Ovládací prvky MFC ActiveX: Advanced témata | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2205862a438099c08801556f511ebf3c5e93a277
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC – ovládací prvky ActiveX: Pokročilá témata
Tento článek se zabývá Pokročilá témata související s vývojem – ovládací prvky ActiveX. Mezi ně patří:  
  
-   [Použití databázových tříd v ovládacích prvcích ActiveX](#_core_using_database_classes_in_activex_controls)  
  
-   [Implementace Parametrizovaná vlastnost](#_core_implementing_a_parameterized_property)  
  
-   [Zpracování chyb ve vašem ovládacím prvku ActiveX](#_core_handling_errors_in_your_activex_control)  
  
-   [Speciální klávesy zpracování v ovládacím prvku](#_core_handling_special_keys_in_your_control)  
  
-   [Přístup k ovládacím prvkům dialogové okno, které jsou neviditelná za běhu](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a>Použití databázových tříd v ovládacích prvcích ActiveX  
 Protože třídy ovládacích prvků ActiveX jsou součástí knihovny tříd, můžete použít stejné postupy a pravidla pro použití databázových tříd ve standardní aplikace MFC k vývoji ovládacích prvků ActiveX, které používají třídami databází MFC.  
  
 Obecné přehled třídami databází MFC, najdete v tématu [třídami databází MFC (rozhraní DAO a ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Článek uvádí třídy knihovny MFC rozhraní ODBC a MFC rozhraní DAO – třídy a vás přesměruje na další informace o buď.  
  
> [!NOTE]
>  Prostředí Visual C++ a průvodců nepodporují rozhraní DAO (i když jsou zahrnuté třídy DAO a můžete je dál používat). Microsoft doporučuje používat [šablony technologie OLE DB](../data/oledb/ole-db-programming.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom pro údržbu existujících aplikací.  
  
##  <a name="_core_implementing_a_parameterized_property"></a>Implementace Parametrizovaná vlastnost  
 Parametrizovaná vlastnost (někdy nazývané vlastnost pole) je metoda pro vystavení homogenní kolekci hodnot jako jedinou vlastností ovládacího prvku. Například můžete Parametrizovaná vlastnost vystavit pole nebo slovník jako vlastnost. V jazyce Visual Basic tato vlastnost přistupuje pomocí notace pole:  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 Implementace Parametrizovaná vlastnost pomocí Průvodce přidáním vlastnosti. Průvodce přidáním vlastnosti implementuje vlastnost přidáním pár Get/Set funkcí, které řízení uživateli umožní získat přístup k vlastnosti pomocí výše uvedených zápisu nebo standardní způsobem.  
  
 Podobá se metod a vlastností, parametrizované vlastnosti také mít limit pro počet parametrů, které jsou povoleny. V případě parametrizované vlastnosti limit je 15 parametry (pomocí parametru jeden vyhrazený pro uložení hodnoty vlastnosti).  
  
 Následující postup přidá Parametrizovaná vlastnost s názvem pole, který je přístupný jako dvourozměrná pole celých čísel.  
  
#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Chcete-li přidat Parametrizovaná vlastnost pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
5.  V **název vlastnosti** zadejte `Array`.  
  
6.  V **typ vlastnosti** vyberte **krátké**.  
  
7.  Pro **implementace** typu, klikněte na tlačítko **metody Get/Set**.  
  
8.  V **získat funkce** a **nastavit funkce** polí zadejte jedinečné názvy pro získání a nastavení funkce nebo přijměte výchozí názvy.  
  
9. Přidat parametr s názvem `row` (typ `short`) pomocí **název parametru** a **typ parametru** ovládací prvky.  
  
10. Přidat druhý parametr s názvem `column` (typ `short`).  
  
11. Klikněte na tlačítko **Dokončit**.  
  
### <a name="changes-made-by-the-add-property-wizard"></a>Změny provedené Průvodce přidáním vlastnosti  
 Když přidáte vlastní vlastnost, Průvodce přidáním vlastnosti provede změny hlavička control – třída (. H) a implementaci (. Soubory CPP).  
  
 Následující řádky se přidají do třídy ovládacího prvku. Soubor H:  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]  
  
 Tento kód deklaruje dvě funkce volané `GetArray` a `SetArray` které umožňují uživatelům při přístupu k vlastnosti požadavku konkrétní řádků a sloupců.  
  
 Kromě toho Průvodce přidáním vlastnosti přidá následující řádky do mapy ovládacího prvku odesílání, umístěný v implementaci třídy ovládacího prvku (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 Nakonec implementace `GetArray` a `SetArray` funkce jsou přidány na konec. Soubor CPP. Ve většině případů budete upravovat Get funkce vrátí hodnotu vlastnosti. Funkce sady bude obvykle obsahovat kód, který by měla spustit před nebo po provedení změn vlastnosti.  
  
 Pro tuto vlastnost, aby byla užitečná, může deklarovat dvourozměrná pole členské proměnné ve třídě ovládacího prvku typu **krátké**, k ukládání hodnot pro Parametrizovaná vlastnost. Může následně upravit funkce Get vrátit s hodnotou uloženou v správné řádků a sloupců, podle parametrů a upravte sadu funkci Aktualizovat hodnotu odkazuje parametry řádků a sloupců.  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a>Zpracování chyb ve vašem ovládacím prvku ActiveX  
 Dojde-li chybové stavy v ovládacím prvku, musíte ohlaste chybu ke kontejneru ovládacího prvku. Existují dvě metody pro zasílání zpráv o chybách, v závislosti na situaci, kdy dojde k chybě. Pokud dojde k chybě v rámci vlastnosti pro získání nebo nastavení funkce, nebo v rámci implementace metodu automatizace OLE, by měly volat ovládacího prvku [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), které signály řízení uživateli, které došlo k chybě. Pokud se vždy, když dojde k chybě, by měly volat ovládacího prvku [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), která aktivuje uložených událost chyby.  
  
 K označení druh chyba, že došlo k chybě, musí projít ovládacího prvku chybový kód k `ThrowError` nebo `FireError`. Kód chyby je stavový kód OLE, což je hodnota 32-bit. Pokud je to možné, vyberte z standardní sadu kódy, které jsou definované v OLECTL chybový kód. Soubor hlaviček H. Následující tabulka shrnuje tyto kódy.  
  
### <a name="activex-control-error-codes"></a>Chybové kódy ovládacího prvku ActiveX  
  
|Chyba|Popis|  
|-----------|-----------------|  
|**CTL_E_ILLEGALFUNCTIONCALL**|Neplatné volání funkce|  
|**CTL_E_OVERFLOW**|Přetečení|  
|**CTL_E_OUTOFMEMORY**|Nedostatek paměti|  
|**CTL_E_DIVISIONBYZERO**|Dělení nulou|  
|**CTL_E_OUTOFSTRINGSPACE**|Nedostatek místa na řetězec|  
|**CTL_E_OUTOFSTACKSPACE**|Nedostatek místa v zásobníku|  
|**CTL_E_BADFILENAMEORNUMBER**|Chybný název souboru nebo číslo|  
|**CTL_E_FILENOTFOUND**|Soubor nebyl nalezen.|  
|**CTL_E_BADFILEMODE**|Chybný režim souboru|  
|**CTL_E_FILEALREADYOPEN**|Soubor již je otevřen.|  
|**CTL_E_DEVICEIOERROR**|Vstupně-výstupní chyba zařízení|  
|**CTL_E_FILEALREADYEXISTS**|Soubor již existuje.|  
|**CTL_E_BADRECORDLENGTH**|Chybná délka záznamu|  
|**CTL_E_DISKFULL**|Disk je plný|  
|**CTL_E_BADRECORDNUMBER**|Počet chybných záznamů|  
|**CTL_E_BADFILENAME**|Chybný název souboru|  
|**CTL_E_TOOMANYFILES**|Příliš mnoho souborů|  
|**CTL_E_DEVICEUNAVAILABLE**|Zařízení není k dispozici|  
|**CTL_E_PERMISSIONDENIED**|Oprávnění byla odepřena.|  
|**CTL_E_DISKNOTREADY**|Disk není připraven|  
|**CTL_E_PATHFILEACCESSERROR**|Chyba přístupu k cestě nebo k souboru|  
|**CTL_E_PATHNOTFOUND**|Cesta nebyla nalezena.|  
|**CTL_E_INVALIDPATTERNSTRING**|Neplatný vzor řetězce|  
|**CTL_E_INVALIDUSEOFNULL**|Neplatné použití hodnoty NULL|  
|**CTL_E_INVALIDFILEFORMAT**|Neplatný formát souboru|  
|**CTL_E_INVALIDPROPERTYVALUE**|Neplatná hodnota vlastnosti|  
|**CTL_E_INVALIDPROPERTYARRAYINDEX**|Neplatný index pole vlastností|  
|**CTL_E_SETNOTSUPPORTEDATRUNTIME**|Nastavit není podporována v době běhu|  
|**CTL_E_SETNOTSUPPORTED**|Nastavte nepodporuje (vlastnost jen pro čtení)|  
|**CTL_E_NEEDPROPERTYARRAYINDEX**|Je vyžadován index pole vlastností.|  
|**CTL_E_SETNOTPERMITTED**|Nastavení není povoleno.|  
|**CTL_E_GETNOTSUPPORTEDATRUNTIME**|Metoda Get není podporována v době běhu|  
|**CTL_E_GETNOTSUPPORTED**|Získat nepodporuje (jen pro zápis vlastnost)|  
|**CTL_E_PROPERTYNOTFOUND**|Vlastnost nebyla nalezena.|  
|**CTL_E_INVALIDCLIPBOARDFORMAT**|Neplatný formát schránky|  
|**CTL_E_INVALIDPICTURE**|Neplatný obrázek|  
|**CTL_E_PRINTERERROR**|Chyba tiskárny|  
|**CTL_E_CANTSAVEFILETOTEMP**|Soubor nelze uložit do dočasného|  
|**CTL_E_SEARCHTEXTNOTFOUND**|Hledaný text nebyl nalezen|  
|**CTL_E_REPLACEMENTSTOOLONG**|Náhrady příliš dlouhý|  
  
 V případě potřeby použít **CUSTOM_CTL_SCODE** makro zadat kód vlastní chyby pro podmínku, která není jedním z standardní kódy. Parametr pro tuto makro musí být celé číslo mezi 1 000 a 32767 (včetně). Příklad:  
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 Pokud vytváříte ovládacího prvku ActiveX k nahrazení existujícího ovládacího prvku VBX, definujte ActiveX chybové kódy ovládacího prvku s stejné číselné hodnoty, které ovládací prvek VBX používá k zajištění souladu kódy chyb.  
  
##  <a name="_core_handling_special_keys_in_your_control"></a>Speciální klávesy zpracování v ovládacím prvku  
 V některých případech můžete chtít zpracování určitých kombinací kláves zvláštním způsobem; například ovládací prvky vložit nový řádek po stisknutí klávesy ENTER víceřádkový text pole ovládací prvek nebo přesunout mezi skupinou upravit, když směru klíče ID stisknutí tlačítka.  
  
 Pokud je základní třída ovládacího prvku ActiveX `COleControl`, můžete přepsat [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) zpracovat zprávy před kontejneru je zpracuje. Pokud použijete tento postup, vždy vrátí **TRUE** Pokud zpracovat zprávu v přepsání z `PreTranslateMessage`.  
  
 Následující příklad kódu ukazuje možný způsob zpracování zpráv, které souvisejí s směrovou klíčů.  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 Další informace o zpracování klávesnice rozhraní pro ovládací prvek ActiveX naleznete v dokumentaci k ActiveX SDK.  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Přístup k ovládacím prvkům dialogové okno, které jsou neviditelná za běhu  
 Můžete vytvořit ovládací prvky dialogového okna, které mají žádné uživatelské rozhraní a jsou neviditelná za běhu. Když přidáte neviditelné v době běhu ovládacího prvku ActiveX na dialogové okno a použít [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pro přístup k ovládacím prvku, ovládacího prvku nebude pracovat správně. Místo toho používejte jednu z následujících postupů získat objekt, který reprezentuje ovládací prvek:  
  
-   Pomocí Průvodce přidáním členské proměnné, vyberte **řízení proměnné** a pak vyberte ID ovládacího prvku. Zadejte název proměnné člena a vyberte třídu obálky ovládacího prvku jako **– typ ovládacího prvku**.  
  
     -nebo-  
  
-   Deklarujte místní proměnné a podtřídami jako položka dialogové okno. Vložení kódu, která se podobá následující (`CMyCtrl` je obálkovou třídu `IDC_MYCTRL1` je ID ovládacího prvku):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

