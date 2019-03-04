---
title: Ovládací prvky ActiveXna Internetu
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: c019c922a5690d4ead861c40bed3c0c1c76cea28
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283001"
---
# <a name="activex-controls-on-the-internet"></a>Ovládací prvky ActiveXna Internetu

Ovládací prvky ActiveX jsou aktualizovanou verzi specifikace ovládacího prvku OLE.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace najdete v tématu [ovládací prvky ActiveX](activex-controls.md).

Ovládací prvky jsou primární architektura pro vývoj programovatelný softwarových komponent, které lze použít v celou řadu různých kontejnerů, včetně s ohledem na COM webových prohlížečů na Internetu. Libovolný ovládací prvek ActiveX může být ovládací prvek Internet a můžete přidat její funkčnosti do aktivního dokumentu nebo část webové stránky. Ovládací prvky na webové stránce mohou vzájemně komunikovat pomocí skriptování.

Ovládací prvky ActiveX nejsou omezeny na Internetu. Ovládací prvek ActiveX lze také v kontejneru, jako ovládací prvek podporuje rozhraní vyžadované tohoto kontejneru.

**Ovládací prvky ActiveX mít několik výhod, včetně:**

- Méně než předchozí ovládací prvky OLE požadovaná rozhraní.

- Možnost být bez oken a vždy místě aktivní.

**Aby byla ovládacího prvku ActiveX, ovládací prvek musí:**

- Podpora `IUnknown` rozhraní.

- Být objekt modelu COM.

- Export **DLLRegisterServer** a **DLLUnRegisterServer**.

- Podpora dalších rozhraní podle potřeby pro funkce.

## <a name="making-your-existing-controls-internet-friendly"></a>Provádění existujících ovládacích prvků vhodných Internet

Návrh ovládacího prvku, který bude fungovat i v prostředí Internetu vyžaduje zvážení, relativně nízký přenosovou rychlostí na Internetu. Můžete použít existující ovládací prvky; Existují však kroky, které byste měli podniknout zmenšit velikost vašeho kódu a chcete-li váš ovládací prvek vlastnosti stáhnout asynchronně.

Chcete-li zvýšit výkon své ovládací prvky, postupujte podle těchto pokynů na efektivitu aspekty:

- Provádění technik popsaných v článku [ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md).

- Zvažte, jak vytvořit instanci ovládacího prvku.

- Být asynchronní; Nedržte jiné programy.

- Stáhněte data v malých blocích.

   Při stahování velkých streamů, jako je například rastrové obrázky nebo obrazových dat, přístup k datům ovládacího prvku asynchronně ve spolupráci s kontejnerem. Načtení dat v přírůstkové, nebo progresivní způsobem spolupráce při práci s jinými ovládacími prvky, které může být načítání dat. Kód můžete stáhnout také asynchronně.

- Stáhněte si kód a vlastnosti na pozadí.

- Stát uživatelského rozhraní active co nejrychleji.

- Vezměte v úvahu jak trvalá data uložená, vlastnosti a velkých objemů dat objektů BLOB (například obrázek nebo video dat rastrového obrázku).

   Ovládací prvky s významné množství trvalá data, jako je například velké rastrové obrázky nebo souborech AVI, vyžadují stahování metoda důkladnou pozornost. Dokumentu nebo na stránce můžete viditelná, co nejdříve a umožnit uživatelům interakci s stránky při načtení dat na pozadí ovládacích prvků.

- Zápis efektivní rutiny zachovat velikost kódu a čas spuštění.

   Malé tlačítko a popisek ovládacích prvků, pomocí jenom pár bajtů trvalá data, jsou vhodné pro použití v prostředí sítě Internet a práce i v prohlížeči.

- Vezměte v úvahu, že probíhá jsou předávány do kontejneru.

   Upozornění pro kontejner probíhá asynchronní stahování, včetně uživatele, můžete začít pracovat na stránce a po dokončení stahování. Kontejner můžete zobrazit průběh (jako procento dokončení) pro uživatele.

- Zvažte, jak ovládací prvky jsou registrované na klientském počítači.

## <a name="creating-a-new-activex-control"></a>Vytvoření nového ovládacího prvku ActiveX

Při vytváření nového ovládacího prvku pomocí Průvodce aplikací, můžete povolit podporu pro asynchronní monikery, stejně jako další optimalizace. Přidání podpory pro stažení ovládacího prvku vlastnosti asynchronně, postupujte takto:

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Chcete-li vytvořit projekt pomocí Průvodce ovládacím prvkem MFC ActiveX

1. Klikněte na tlačítko **nový** na **souboru** nabídky.

1. Vyberte **Průvodce ovládacím prvkem MFC ActiveX** projekty v jazyce Visual C++ a pojmenujte svůj projekt.

1. Na **nastavení** stránce **asynchronně načte vlastnosti**. Výběrem této možnosti nastavíte vlastnost připraveném stavu a událostí změny stavu připraveno za vás.

   Můžete také vybrat další optimalizace, jako například **aktivace bez oken**, který je popsaný v [ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md).

1. Zvolte **Dokončit** pro vytvoření projektu.

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Chcete-li vytvořit třídu odvozenou z cdatapathproperty –

1. Vytvoření třídy odvozené od `CDataPathProperty`.

1. V každém ze zdrojových souborů, které obsahuje soubor záhlaví ovládacího prvku přidejte hlavičkový soubor pro tuto třídu před ní.

1. V této třídě přepsat `OnDataAvailable`. Tato funkce je volána pokaždé, když se data jsou k dispozici k zobrazení. Jak budou data k dispozici, je možné ji zpracovávat žádným způsobem, který zvolíte, například postupně vykreslování.

   Výpis kódu níže je jednoduchý příklad postupně zobrazení dat v ovládacím prvku upravovat. Všimněte si použití příznaku **BSCF_FIRSTDATANOTIFICATION** zrušte textové pole.

   [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   Všimněte si, že musí obsahovat AFXCMN. H používat `CListCtrl` třídy.

1. Pokud ovládacího prvku celkový stav se změní (například v načtení do inicializovaného nebo interaktivní uživatel), volání `COleControl::InternalSetReadyState`. Pokud váš ovládací prvek má pouze jednu datovou Vlastnost path, můžete přidat kód na **BSCF_LASTDATANOTIFICATION** oznámit kontejneru dokončení stahování. Příklad:

   [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. Přepsat `OnProgress`. V `OnProgress`, jsou předány číslo zobrazující maximální rozsah a je číslo znázorňující, jak daleko podél aktuální soubor ke stažení. Tato čísla slouží k zobrazení stavu, jako je například procento dokončení uživateli.

Další postup přidá vlastnost do ovládacího prvku pomocí právě odvozené třídy.

#### <a name="to-add-a-property"></a>Přidání vlastnosti

1. V **zobrazení tříd**, klikněte pravým tlačítkem na rozhraní pod tímto uzlem knihovny a vyberte **přidat**, pak **přidat vlastnost**. Tím se spustí **Průvodce přidáním vlastnosti**.

1. V **Průvodce přidáním vlastnosti**, vyberte **Set/Get metody** přepínací tlačítko, zadejte **název vlastnosti**, například EditControlText a vyberte BSTR jako **Typ vlastnosti**.

1. Klikněte na tlačítko **Dokončit**.

1. Deklarujte proměnné člena vaší `CDataPathProperty`-odvozené třídy a třídy vašeho ovládacího prvku ActiveX.

   [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. Implementace `Get/Set` metody. Pro `Get`, vrátí řetězec. Pro `Set`, načtení vlastností a volání `SetModifiedFlag`.

   [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. V [DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange), přidejte následující řádek:

   [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. Přepsat [ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata) oznámit vlastnost resetování ovládacího prvku tak, že přidáte tento řádek:

   [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Rozhodování o tom, jestli se má odvodit z cdatapathproperty – nebo ccacheddatapathproperty –

Předchozí příklad popisuje kroky pro odvození vlastnost ovládacího prvku z `CDataPathProperty`. Toto je dobrou volbou, pokud stahujete dat v reálném čase, který se často mění, a pro kterou nepotřebujete ponechte všechna data, ale pouze aktuální hodnotu. Příkladem je ovládací prvek akciích.

Můžete také provádět odvozování z `CCachedDataPathProperty`. V takovém případě stažených dat do mezipaměti v paměti souboru. Toto je dobrou volbou, pokud je potřeba nechat stažených dat – například ovládací prvek, který vykreslí postupně rastrový obrázek. V takovém případě třída nemá členskou proměnnou obsahující vaše data:

`CMemFile m_Cache;`

Ve třídě ovládacího prvku ActiveX, můžete použít tento soubor mapované paměti v `OnDraw` zobrazit data. V ovládacím prvku ActiveX `CCachedDataPathProperty`-odvozené třídy, členské funkce přepsat `OnDataAvailable` a zneplatnit ovládacího prvku, po volání implementace základní třídy.

[!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>Stahování dat asynchronně pomocí ovládacích prvků ActiveX

Stahování dat přes síť by měla být provedena asynchronně. Výhodou to tak je, že pokud přenos velkých objemů dat nebo pokud je pomalé připojení, proces stahování nezablokuje jiné procesy na straně klienta.

Asynchronní monikery poskytují způsob, jak stahovat data asynchronně přes síť. Operace čtení na asynchronní moniker vrátí hodnotu okamžitě, i v případě, operace nebyla dokončena.

Například pokud pouze 10 bajtů je k dispozici a čtení je volána asynchronně v souboru 1 kB, čtení nedochází k blokování, ale vrátí se v současnosti 10 bajtů.

Můžete implementovat [asynchronní monikery](../mfc/asynchronous-monikers-on-the-internet.md) pomocí `CAsyncMonikerFile` třídy. Ale můžete použít ovládací prvky ActiveX `CDataPathProperty` třídu, která je odvozena od `CAsyncMonikerFile`, implementaci asynchronního ovládacího prvku vlastnosti.

## <a name="displaying-a-control-on-a-web-page"></a>Zobrazení ovládacího prvku na webové stránce

Tady je příklad značka objektu a atributů pro vložení ovládacího prvku na webové stránce.

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Aktualizace existujícího ovládacího prvku OLE používat nové funkce ovládacího prvku ActiveX

Pokud váš ovládací prvek OLE byl vytvořen s verzí jazyka Visual C++ před 4.2, existují kroky, které můžete provést při jeho výkon a zvýšit jeho funkce. Podrobné informace o těchto změnách najdete v části [ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md).

Pokud přidáváte podporu asynchronního vlastnost do existujícího ovládacího prvku, je potřeba přidat vlastnost připraveném stavu a `ReadyStateChange` události sami. V konstruktoru pro ovládací prvek přidejte:

[!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

Budete připraveni aktualizovat váš kód je stažené voláním [COleControl::InternalSetReadyState](../mfc/reference/colecontrol-class.md#internalsetreadystate). Jedno místo, které lze volat `InternalSetReadyState` z `OnProgress` přepsání `CDataPathProperty`-odvozené třídy.

## <a name="see-also"></a>Viz také:

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)
