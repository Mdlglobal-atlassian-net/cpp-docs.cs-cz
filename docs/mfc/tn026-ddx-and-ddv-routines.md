---
title: 'TN026: Rutiny DDX a DDV'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370336"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: Rutiny DDX a DDV

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje architekturu výměny dat dialogových oken (DDX) a ověření dat dialogových dat (DDV). Také popisuje, jak napsat DDX_ nebo DDV_ postup a jak můžete rozšířit ClassWizard používat rutiny.

## <a name="overview-of-dialog-data-exchange"></a>Přehled výměny dialogových dat

Všechny funkce dialogových dat jsou prováděny s kódem Jazyka C++. Neexistují žádné speciální zdroje nebo magická makra. Srdcem mechanismu je virtuální funkce, která je přepsána v každé třídě dialogu, která provádí výměnu a ověřování dat dialogu. Vždy se nachází v této podobě:

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

Speciální formát Komentáře AFX umožňují ClassWizard najít a upravit kód v rámci této funkce. Kód, který není kompatibilní s ClassWizard by měl být umístěn mimo komentář speciální formát.

Ve výše uvedeném příkladu \<je data_exchange_function_call> ve formě:

```cpp
DDX_Custom(pDX, nIDC, field);
```

a \<data_validation_function_call> je nepovinné a je ve formě:

```cpp
DDV_Custom(pDX, field, ...);
```

Do každé `DoDataExchange` funkce může být zahrnuto více než jeden pár DDX_/DDV_.

Seznam všech rutin výměny dialogových dat a rutin ověřování dat dialogových oken, které jsou součástí knihovny MFC, naleznete v tématu afxdd_.h.

Dialogová data je právě to: data členů ve `CMyDialog` třídě. Není uložen ve struktuře nebo něco podobného.

## <a name="notes"></a>Poznámky

Přestože nazýváme tento "dialog data", všechny funkce `CWnd` jsou k dispozici v jakékoli třídě odvozené z a nejsou omezeny pouze na dialogy.

Počáteční hodnoty dat jsou nastaveny ve standardním konstruktoru `//{{AFX_DATA_INIT` C++, obvykle v bloku s a `//}}AFX_DATA_INIT` komentáře.

`CWnd::UpdateData`je operace, která provádí inicializaci a `DoDataExchange`zpracování chyb kolem volání .

Můžete kdykoli `CWnd::UpdateData` volat a provádět výměnu a ověřování dat. Ve `UpdateData`výchozím nastavení (TRUE) `CDialog::OnOK` se `UpdateData`nazývá ve výchozí obslužné rutině a (FALSE) je volána ve výchozím nastavení `CDialog::OnInitDialog`.

Rutina DDV_ by měla okamžitě dodržovat DDX_ rutinu pro *toto pole*.

## <a name="how-does-it-work"></a>Jak to funguje

Chcete-li použít data dialogu, nemusíte porozumět následujícím. Pochopení toho, jak to funguje na pozadí, vám však pomůže napsat vlastní postup výměny nebo ověření.

Členská `DoDataExchange` funkce je `Serialize` podobně jako členská funkce - je zodpovědná za získání nebo nastavení dat do/z externího formuláře (v tomto případě ovládacíprvky v dialogu) z/do členských dat ve třídě. Parametr *pDX* je kontext pro výměnu dat a `CArchive` je `CObject::Serialize`podobný parametru . *PDX* `CDataExchange` (objekt) má směr příznak `CArchive` podobně jako má směr příznak:

- Pokud `!m_bSaveAndValidate`, načtěte stav dat do ovládacích prvků.

- Pokud `m_bSaveAndValidate`, nastavte stav dat z ovládacích prvků.

K ověření dochází `m_bSaveAndValidate` pouze v případě, že je nastavena. Hodnota `m_bSaveAndValidate` je určena parametrem BOOL `CWnd::UpdateData`do .

Existují tři další `CDataExchange` zajímaví členové:

- `m_pDlgWnd`: Okno (obvykle dialogové okno), které obsahuje ovládací prvky. To to je zabránit volající min. DDX_ a DDV_ globální funkce museli předat 'to' do každé rutiny DDX/DDV.

- `PrepareCtrl`, `PrepareEditCtrl`a : Připraví ovládací prvek dialogového okna pro výměnu dat. Ukládá popisovač tohoto ovládacího prvku pro nastavení fokusu, pokud se ověření nezdaří. `PrepareCtrl`se používá pro neupravované ovládací prvky a `PrepareEditCtrl` používá se pro ovládací prvky pro úpravy.

- `Fail`: Voláno po zobrazení okna se zprávou upozorňujícího uživatele na vstupní chybu. Tato rutina obnoví fokus na poslední ovládací `PrepareCtrl` `PrepareEditCtrl`prvek (poslední volání nebo ) a vyvolá výjimku. Tato členská funkce může být volána z DDX_ i DDV_ rutiny.

## <a name="user-extensions"></a>Uživatelská rozšíření

Existuje několik způsobů, jak rozšířit výchozí mechanismus DDX/DDV. Můžete:

- Přidejte nové datové typy.

    ```cpp
    CTime
    ```

- Přidejte nové postupy výměny (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Přidejte nové ověřovací postupy (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Předajte libovolné výrazy ověřovacím postupům.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Tyto libovolné výrazy nelze upravovat ClassWizard a proto by měly být přesunuty mimo komentář speciální formát (/{{AFX_DATA_MAP(CMyClass)).

Mají `DoDialogExchange` členské funkce zahrnout podmínky nebo jiné platné příkazy Jazyka C++ s propletené volání exchange a validační funkce.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> Jak je uvedeno výše, takový kód nelze upravit ClassWizard a by měl být použit pouze mimo komentář speciální formát.

## <a name="classwizard-support"></a>Podpora průvodce třídami

ClassWizard podporuje podmnožinu ddx/DDV přizpůsobení tím, že umožňuje integrovat vlastní DDX_ a DDV_ rutiny do uživatelského rozhraní ClassWizard. To je výhodné pouze pro nákladově výhodné, pokud plánujete znovu použít konkrétní rutiny DDX a DDV v projektu nebo v mnoha projektech.

Chcete-li to provést, jsou v DDX provedeny speciální položky. CLW (předchozí verze visual c++ uložené tyto informace v APSTUDIO. INI) nebo v projektu . CLW. Speciální položky lze zadat buď do oddílu [Obecné informace] projektu . CLW nebo v části [ExtraDDX] ddx. Soubor CLW v adresáři \Program Files\Microsoft Visual Studio\Visual C++\bin. Možná budete muset vytvořit DDX. CLW, pokud ještě neexistuje. Pokud plánujete používat vlastní rutiny DDX_/DDV_ pouze v určitém projektu, přidejte položky do oddílu [Obecné informace] projektu . CLW soubor místo. Pokud plánujete používat rutiny v mnoha projektech, přidejte položky do sekce [ExtraDDX] ddx. Clw.

Obecný formát těchto speciálních položek je:

> ExtraDDXCount =*n*

kde *n* je počet ExtraDDX? řádky, které chcete sledovat, formuláře

> ExtraDDX?=*klávesy*; *vb-klíče*; *výzva*; *typ*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *výzva1*; *arg1* [; *výzva2*; *fmt2*]]

Kde? je číslo 1 - *n* označující, který typ DDX v seznamu, který je definován.

Každé pole je odděleno znakem ';'. Pole a jejich účel jsou popsány níže.

- *keys*

  Seznam jednotlivých znaků označující, pro které dialogové okno ovládá tento typ proměnné je povolen.

  |Znak|Povolené řízení|
  |-|-|
  E | upravit
  C | dvoustavové zaškrtávací políčko
  c | třístavové zaškrtávací políčko
  R | první přepínací tlačítko ve skupině
  L | seznam bez řazení
  l | seřazený seznam
  M | pole se seznamem (s položkou pro úpravy)
  Ne | neseřazený seznam přetažení
  n | seřazený seznam přetažení
  1 | pokud ddx vložit by měl y být přidány do hlavy seznamu (výchozí je přidat do ocasu) To se obecně používá pro rutiny DDX, které přenášejí 'Control' vlastnost.

- *vb-klíče*

  Toto pole se používá pouze v 16bitovém produktu pro ovládací prvky VBX (ovládací prvky VBX nejsou v 32bitovém produktu podporovány)

- *Výzva*

  Řetězec, který chcete umístit do pole se seznamem Vlastnosti (bez uvozovek)

- *Typ*

  Jediný identifikátor pro typ, který má být vyzařován v souboru záhlaví. V našem příkladu výše s DDX_Time by to bylo nastaveno na CTime.

- *vb-klíče*

  Nepoužívá se v této verzi a měl by být vždy prázdný

- *initValue*

  Počáteční hodnota — 0 nebo prázdné. Pokud je prázdný, nebude v části //{{AFX_DATA_INIT souboru implementace zapsán žádný řádek inicializace. Pro objekty jazyka C++ (například `CString` `CTime`, a tak dále), které mají konstruktory, které zaručují správnou inicializaci, by měla být použita prázdná položka.

- *DDX_Proc*

  Jednotný identifikátor pro DDX_ proceduru. Název funkce Jazyka C++ musí začínat "DDX_", ale \<do identifikátoru DDX_Proc> nezahrnujte "DDX_". Ve výše uvedeném \<příkladu by DDX_Proc> identifikátorem čas. Když ClassWizard zapíše volání funkce do souboru implementace v {{AFX_DATA_MAP části, připojí tento název k DDX_, a tím přichází na DDX_Time.

- *Komentář*

  Komentář, který se zobrazí v dialogu pro proměnnou s tímto DDX. Místo jakýkoli text, který chcete sem, a obvykle poskytují něco, co popisuje operaci prováděnou ddx/ DDV dvojice.

- *DDV_Proc*

  Část položky DDV je nepovinná. Ne všechny rutiny DDX mají odpovídající rutiny DDV. Často je vhodnější zahrnout fázi ověření jako nedílnou součást přenosu. To je často případ, kdy vaše rutina DDV nevyžaduje žádné parametry, protože ClassWizard nepodporuje rutiny DDV bez jakýchkoli parametrů.

- *Arg*

  Jednotný identifikátor pro DDV_ postup. Název funkce Jazyka C++ musí začínat "DDV_", ale \<do identifikátoru DDX_Proc> neobsahuje "DDX_".

  *arg* následuje 1 nebo 2 DDV args:

  - *promptN*

      Řetězec umístit nad položku úprav (s & pro akcelerátor).

  - *fmtN*

      Formát znaku pro typ arg, jeden z:

      |Znak|Typ|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | long int (to znamená, že dlouhé)|
      |U | dlouho nepodepsané (to znamená DWORD)|
      |f | float|
      |F | double|
      |s | řetězec|

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
