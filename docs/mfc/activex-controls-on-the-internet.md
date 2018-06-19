---
title: ActiveX – ovládací prvky na Internetu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a42a7bc042301cfbd7d62f82b7c676686146850
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352305"
---
# <a name="activex-controls-on-the-internet"></a>Ovládací prvky ActiveXna Internetu
ActiveX – ovládací prvky jsou aktualizovanou verzi specifikace OLE ovládacího prvku. Ovládací prvky jsou primární architektury pro vývoj programovatelný softwarové komponenty, které lze použít v různých různé kontejnery, včetně podporující rozhraní COM webových prohlížečů na Internetu. Libovolný ovládací prvek ActiveX může být ovládací prvek Internet a můžete přidat jeho funkce pro aktivní dokument nebo být součástí webové stránky. Ovládací prvky na webové stránce mohou komunikovat navzájem pomocí skriptování.  
  
 ActiveX – ovládací prvky nejsou omezeny na Internetu. Ovládací prvek ActiveX lze také v jakékoli kontejneru ovládacího prvku podporuje rozhraní, které vyžadují tento kontejner.  
  
 **ActiveX – ovládací prvky mít několik výhod, včetně:**  
  
-   Méně než předchozí ovládací prvky OLE požadovaná rozhraní.  
  
-   Schopnost se bez oken a aktivní vždy na místě.  
  
 **Chcete-li být ovládací prvek ActiveX, musíte ovládacího prvku:**  
  
-   Podpora **IUnknown** rozhraní.  
  
-   Být objekt modelu COM.  
  
-   Export **DLLRegisterServer** a **DLLUnRegisterServer**.  
  
-   Podle potřeby pro funkci podporovat další rozhraní.  
  
## <a name="making-your-existing-controls-internet-friendly"></a>Tvorba Internet-Friendly vaší existující ovládacích prvků  
 Navrhování ovládacího prvku, který bude fungovat i v prostředí Internetu vyžaduje zvážení, nízkou přenosovou rychlostí na Internetu. Můžete použít stávající ovládací prvky; Existují však kroky, které byste měli vzít zmenšit velikost vašeho kódu a aby se vaše – vlastnosti ovládacích prvků stáhnout asynchronně.  
  
 Ke zlepšení výkonu pro vaše ovládací prvky, postupujte podle těchto tipy na efektivitu aspekty:  
  
-   Implementace technik popsaných v článku [– ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md).  
  
-   Zvažte, jak je vytvořena instance ovládacího prvku.  
  
-   Být asynchronní; Nemáte podržte si jiné programy.  
  
-   Stahování dat v malých bloky.  
  
     Při stahování velké datové proudy, jako jsou rastrové obrázky nebo video dat, přístup k datům ovládacího prvku asynchronně ve spolupráci s kontejneru. Načtení dat v přírůstkové nebo progresivní způsobem spolupráce při práci s další ovládací prvky, které může být načítání dat. Kód můžete také stáhnout asynchronně.  
  
-   Stáhněte si kód a vlastnosti na pozadí.  
  
-   Uživatelské rozhraní stane aktivní co nejrychleji.  
  
-   Vezměte v úvahu jak trvalá data uložena, vlastnosti a velkého množství dat objektů BLOB (například obrázek nebo video dat rastrový obrázek).  
  
     Ovládací prvky s poměrně velké množství trvalá data, jako třeba velké Bitmap nebo souborů AVI vyžadují pečlivé stahování metoda. Stránka nebo dokument může budou zobrazeny co nejdříve a povolit uživatelům interakci se stránkou při ovládací prvky načtení dat na pozadí.  
  
-   Zápis efektivní rutiny běh a udržování velikosti kódu.  
  
     Malé a popisek ovládacích prvků, se pouze několik bajtů dat, jsou vhodné pro použití v prostředí Internetu a pracovní i v prohlížeči.  
  
-   Vezměte v úvahu, že probíhá informace se předávají do kontejneru.  
  
     Upozorněte kontejneru průběh asynchronní stahování, včetně uživatele můžete začít pracovat se stránkou, a po dokončení stahování. Kontejner můžete zobrazit průběh (jako procento dokončení) pro uživatele.  
  
-   Zvažte, jak jsou registrované ovládací prvky v klientském počítači.  
  
## <a name="creating-a-new-activex-control"></a>Vytvoření nového ovládacího prvku ActiveX  
 Při vytváření nového ovládacího prvku s použitím Průvodce aplikace, můžete povolit podporu pro asynchronní monikery, jakož i další optimalizace. Chcete-li přidat podporu asynchronně stáhnout – vlastnosti ovládacích prvků, postupujte takto:  
  
#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Vytvoření projektu pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC  
  
1.  Klikněte na tlačítko `New` na **souboru** nabídky.  
  
2.  Vyberte **Průvodce ovládacím prvkem ActiveX knihovny MFC** z Visual C++ projekty a název projektu.  
  
3.  Na **nastavení řízení** vyberte **asynchronně načte vlastnosti**. Výběrem této možnosti nastavíte vlastnost připraveném stavu a událostí změny stavu Připraveno pro vás.  
  
     Můžete také vybrat další optimalizace, jako například **aktivace bez oken**, které je popsáno v [– ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md).  
  
4.  Zvolte **Dokončit** a vytvořte tak projekt.  
  
#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Vytvoření třídy odvozené od CDataPathProperty  
  
1.  Vytvoření třídy odvozené od `CDataPathProperty`.  
  
2.  V každé z vaší zdrojové soubory, které obsahuje soubor hlaviček pro ovládací prvek přidejte soubor hlavičky pro tuto třídu před ním.  
  
3.  V této třídě přepsat `OnDataAvailable`. Tato funkce je volána, když jsou k dispozici pro zobrazení data. Jakmile data k dispozici, můžete ji zpracovat jakýmkoli způsobem, kterou zvolíte, například progresivně vykreslit ho.  
  
     Výňatek ze kódu níže je jednoduchý příklad progresivně zobrazení dat v ovládacím prvku upravit. Všimněte si použití příznak **BSCF_FIRSTDATANOTIFICATION** zrušte ovládací prvek upravit.  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]  
  
     Všimněte si, že je nutné zahrnout AFXCMN. H používat `CListCtrl` třídy.  
  
4.  Pokud ovládacího prvku celkový stav změní (například z načítání do inicializována nebo interaktivní uživatele), volání `COleControl::InternalSetReadyState`. Pokud má vlastní ovládací prvek pouze jeden datový vlastností path, můžete přidat kód na **BSCF_LASTDATANOTIFICATION** oznámit kontejneru, stahování je dokončena. Příklad:  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]  
  
5.  Přepsání `OnProgress`. V `OnProgress`, se předávají číslo zobrazující maximální rozsah a je číslo znázorňující, jak daleko podél aktuální stahování. Tato čísla můžete použít k zobrazení stavu, jako je například procento dokončení uživateli.  
  
 V dalším postupu přidá vlastnosti do ovládacího prvku použití právě odvozené třídy.  
  
#### <a name="to-add-a-property"></a>Chcete-li přidat vlastnost  
  
1.  V **zobrazení tříd**, klikněte pravým tlačítkem na rozhraní pod tímto uzlem knihovny a vyberte **přidat**, pak **přidat vlastnost**. Tato akce spustí **Průvodce přidáním vlastnosti**.  
  
2.  V **Průvodce přidáním vlastnosti**, vyberte **Set/Get metody** přepínač, zadejte **název vlastnosti**, například EditControlText, a vyberte BSTR jako **Typ vlastnosti**.  
  
3.  Klikněte na tlačítko **Dokončit**.  
  
4.  Deklarovat členské proměnné z vaší `CDataPathProperty`-odvozené třídy ke třídě ovládacího prvku ActiveX.  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]  
  
5.  Implementace **Get/Set** metody. Pro **získat**, vrátí řetězec. Pro `Set`, načtení vlastností a volání `SetModifiedFlag`.  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]  
  
6.  V [dopropexchange –](../mfc/reference/colecontrol-class.md#dopropexchange), přidejte následující řádek:  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]  
  
7.  Přepsání [ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata) oznámit vlastnost, která má obnovit jeho ovládacího prvku tak, že přidáte tento řádek:  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]  
  
## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Rozhodování, zda jsou odvozeny od CDataPathProperty nebo CCachedDataPathProperty  
 Předchozí příklad popisuje kroky pro odvození ovládacího prvku vlastnost z `CDataPathProperty`. Toto je vhodné použít, pokud stahujete data v reálném čase, který se často mění a pro které není nutné zachovat všechna data, ale pouze aktuální hodnotu. Příkladem je běžícími ovládacího prvku.  
  
 Můžete také odvodit z `CCachedDataPathProperty`. V takovém případě stažená data se uloží do mezipaměti v paměti souboru. To je vhodné použít, pokud je třeba zachovat stažených dat – například ovládací prvek, který vykreslí progresivně rastrový obrázek. V takovém případě má třída členské proměnné obsahující data:  
  
 `CMemFile m_Cache;`  
  
 Ve třídě ovládacího prvku ActiveX můžete použít tento soubor mapované paměti v `OnDraw` a zobrazí data. Ve vašem ovládacím prvku ActiveX `CCachedDataPathProperty`-odvozené třídy, přepsání – členská funkce `OnDataAvailable` a zneplatnit ovládacího prvku, po volání metody implementaci základní třídy.  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]  
  
## <a name="downloading-data-asynchronously-using-activex-controls"></a>Stahování dat asynchronně použití ovládacích prvků ActiveX  
 Stahování dat přes síť by mělo být provedeno asynchronně. Výhodou to tak je, že pokud se přenáší velké množství dat nebo pokud je připojení pomalým, procesu stahování se nebude blokovat jiné procesy na straně klienta.  
  
 Asynchronní monikery poskytují způsob, jak asynchronně stahování dat přes síť. Operace čtení na asynchronní Přezdívka vrátí okamžitě, i v případě, že operace nebyla dokončena.  
  
 Například pokud jenom 10 bajtů je k dispozici a pro čtení se asynchronně volá na soubor 1 kB, čtení neblokuje, ale vrátí s aktuálně dostupné bajty 10.  
  
 Můžete implementovat [asynchronní monikery](../mfc/asynchronous-monikers-on-the-internet.md) pomocí `CAsyncMonikerFile` třídy. Ale můžete použít ovládací prvky ActiveX `CDataPathProperty` třídy, která je odvozená od `CAsyncMonikerFile`, pomohou implementovat asynchronní řízení vlastnosti.  
  
 Ukázka ASYNDOWN ukazuje, jak nastavit smyčky asynchronní pomocí časovačů přečíst data. ASYNDOWN je podrobně popsaná v článku znalostní báze "Postupy: AsyncDown ukazuje asynchronní Data stáhnout" (Q177244) a je k dispozici ke stažení z webu Microsoft Download Center. (Další informace o stahování souborů z webu Microsoft Download Center, najdete v článku "Jak k získání souborů z Online služby podpory" (Q119591) znalostní báze Microsoft Knowledge Base.) Můžete najít články znalostní báze Knowledge Base na [ http://support.microsoft.com/support ](http://support.microsoft.com/support).  
  
 Základní postup používá v ASYNDOWN je nastavit časovač **CDataPathProperty::OnDataAvailable** k označení, když je k dispozici data. Po přijetí zprávy časovače aplikace čtení 128 bajtů bloků dat a výplní ovládací prvek upravit. Data nejsou k dispozici, pokud je zpráva časovače, časovač vypnutý. `OnDataAvailable` spustí časovač, pokud další data dorazí později.  
  
## <a name="displaying-a-control-on-a-web-page"></a>Zobrazení ovládacího prvku na webové stránce  
 Tady je příklad značky a atributy pro vložení ovládacího prvku na webové stránce.  
  
 `<OBJECT`  
  
 `CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"`  
  
 `CODEBASE="/ie/download/activex/iechart.ocx"`  
  
 `ID=chart1`  
  
 `WIDTH=400`  
  
 `HEIGHT=200`  
  
 `ALIGN=center`  
  
 `HSPACE=0`  
  
 `VSPACE=0`  
  
 `>`  
  
 `<PARAM NAME="BackColor" value="#ffffff">`  
  
 `<PARAM NAME="ForeColor" value="#0000ff">`  
  
 `<PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt">`  
  
 `</OBJECT>`  
  
## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Aktualizace existujícího ovládacího prvku OLE používat nové funkce ovládacího prvku ActiveX  
 Pokud OLE ovladač byl vytvořen s verzí aplikace Visual C++ před 4.2, existují kroky, které můžete provést na jeho výkon a zdokonalování jeho funkce. Podrobnou diskuzi o tyto změny, najdete v části [– ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md).  
  
 Pokud přidáváte podporu asynchronní vlastnost do existujícího ovládacího prvku, budete muset přidat vlastnost stavu Připraveno a `ReadyStateChange` událostí sami. V konstruktoru pro ovládací prvek přidejte:  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]  
  
 Aktualizujte stavu Připraveno jako kódu se stáhne voláním [COleControl::InternalSetReadyState](../mfc/reference/colecontrol-class.md#internalsetreadystate). Jednom místě, může volat `InternalSetReadyState` z `OnProgress` přepsat z `CDataPathProperty`-odvozené třídy.  
  

  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

