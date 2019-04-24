---
title: 'TN026: DDX a DDV'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 89916e60d9677240f2d70e37e9a80e6ad7a76fc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305863"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: DDX a DDV

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje výměna dat dialogových oken (DDX) a architektura ověření (DDV) dat dialogového okna. Také popisuje, jak psát DDX_ nebo DDV_ procedury a jak můžete rozšířit ClassWizard používat vaše rutiny.

## <a name="overview-of-dialog-data-exchange"></a>Přehled výměna dat dialogových oken

Všechny funkce dat dialogových oken se provádějí s kódem jazyka C++. Neexistují žádné zvláštní prostředky nebo magic makra. Srdce mechanismu, který je virtuální funkce, která je přepsána v každé třídy dialogového okna, aby se výměna dialogových dat a ověřování. Vždy nachází v tomto formuláři:

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

Afx – komentáře zvláštní formát umožňují ClassWizard k vyhledání a úpravy kódu v rámci této funkce. Kód, který není kompatibilní s ClassWizard by měl umístit mimo speciální formátu komentáře.

Ve výše uvedeném příkladu \<data_exchange_function_call > je ve formátu:

```cpp
DDX_Custom(pDX, nIDC, field);
```

a \<data_validation_function_call > je volitelná a má formát:

```cpp
DDV_Custom(pDX, field, ...);
```

Více než jednu dvojici DDX_/DDV_ může být součástí každého `DoDataExchange` funkce.

Seznam všech rutiny výměny dat dialogového okna a rutiny ověřování dat dialogového okna je k dispozici s knihovnou MFC naleznete v tématu "afxdd_.h".

Data dialogového okna je přesně to: data členů v `CMyDialog` třídy. Už se neukládají v struktury nebo žádné další obdoby.

## <a name="notes"></a>Poznámky

I když tento "dat dialogových oken" říkáme, všechny funkce jsou k dispozici v libovolné třídě odvozené z `CWnd` a nejsou omezeny pouze dialogy.

Počáteční hodnoty dat jsou nastavené v konstruktoru standard C++, obvykle v bloku s `//{{AFX_DATA_INIT` a `//}}AFX_DATA_INIT` komentáře.

`CWnd::UpdateData` operace, která provádí inicializace a kolem volání pro zpracování chyb `DoDataExchange`.

Můžete volat `CWnd::UpdateData` kdykoli k provedení výměny dat a ověřování. Ve výchozím nastavení `UpdateData`(pravda), se nazývá ve výchozím `CDialog::OnOK` obslužné rutiny a `UpdateData`(FALSE) je ve výchozím názvem `CDialog::OnInitDialog`.

Rutina DDV_ okamžitě postupujte podle DDX_ rutiny pro daný *pole*.

## <a name="how-does-it-work"></a>Jak to funguje

Nemusíte pochopit následující, abyste mohli používat dat dialogových oken. Ale pochopení, jak to funguje na pozadí můžete napsat vlastní postup ověření nebo exchange.

`DoDataExchange` Členská funkce je stejně jako `Serialize` členské funkce – je zodpovědný za získání nebo nastavení dat do a z externích formuláře (ovládací prvky v tomto případě v dialogovém okně) z/do data členů ve třídě. *PDX* parametr je kontext pro provedení výměny dat a je podobný `CArchive` parametr `CObject::Serialize`. *PDX* ( `CDataExchange` objekt) má směr příznak mnohem jako `CArchive` má příznak směru:

- Pokud `!m_bSaveAndValidate`, načtěte data stavu do ovládacích prvků.

- Pokud `m_bSaveAndValidate`, pak nastavte stav dat z ovládacích prvků.

Ověření dochází pouze při `m_bSaveAndValidate` nastavena. Hodnota `m_bSaveAndValidate` určuje parametr typu BOOL na `CWnd::UpdateData`.

Existují tři další zajímavé `CDataExchange` členy:

- `m_pDlgWnd`: V okně (obvykle dialogového okna), který obsahuje ovládací prvky. To je zabránit volající globální funkce DDX_ a DDV_ s k předání 'this' na každá rutina DDX/DDV.

- `PrepareCtrl`, a `PrepareEditCtrl`: Připraví ovládací prvek dialogového okna pro data systému exchange. Uloží popisovač tohoto ovládacího prvku nastavení fokusu, pokud se ověřování nezdaří. `PrepareCtrl` se používá pro jiné ovládací prvky a `PrepareEditCtrl` se používá pro ovládacích prvcích pro úpravy.

- `Fail`: Volá se po přepnutí do okna se zprávou upozornění uživateli vstupních chyb. Tato rutina obnoví fokus na poslední ovládací prvek (poslední volání `PrepareCtrl` nebo `PrepareEditCtrl`) a vyvolají výjimku. Tato členská funkce může být volána z DDX_ a DDV_ rutiny.

## <a name="user-extensions"></a>Rozšíření uživatele

K rozšíření výchozího mechanismu DDX/DDV několika způsoby. Můžete:

- Přidáte nové datové typy.

    ```cpp
    CTime
    ```

- Přidáte nové postupy exchange (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Přidáte nové ověřovací procedury (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Libovolné výrazy předejte postupy ověření.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Takové libovolné výrazy nelze upravit pomocí ClassWizard a proto by měl být přesunut mimo speciální formátu komentáře (/ / {{AFX_DATA_MAP(CMyClass)).

Máte `DoDialogExchange` členská funkce patří podmíněné výrazy nebo jakékoli jiné platné příkazy C++ s míchán výměna a ověřování volání funkce.

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
> Jak uvádíme výš, takový kód nelze upravit pomocí ClassWizard a měli použít pouze vně speciální formátu komentáře.

## <a name="classwizard-support"></a>Podpora ClassWizard

ClassWizard podporuje podmnožinu DDX/DDV přizpůsobení, neboť umožňuje integrovat vlastní DDX_ a DDV_ rutin do uživatelského rozhraní ClassWizard. To je jenom náklady na výhodné, pokud budete chtít znovu použít konkrétní DDX a DDV rutiny v projektu nebo v mnoha projektů.

K tomu dojde ke speciální položky ve DDX. CLW (předchozí verze aplikace Visual C++ uložené tyto informace v APSTUDIO. INI) nebo ve vašem projektu. CLW souboru. Speciální položky může být zadán buď v [obecné informace o] části vašeho projektu. CLW souboru nebo v části [ExtraDDX] DDX. Soubor CLW \Program Files\Microsoft Visual Studio\Visual C++adresáři \bin. Budete muset vytvořit DDX. CLW soubor, pokud ještě neexistuje. Pokud budete chtít použít vlastní rutiny DDX_/DDV_ pouze v určitých projektu, přidejte položky do oddílu [obecné informace o] vašeho projektu. CLW souboru místo toho. Pokud máte v plánu pro použití rutin na mnoho projektů, přidáte položky do oddílu [ExtraDDX] DDX. CLW.

Je obecný formát tyto speciální položky:

> ExtraDDXCount=*n*

kde *n* je počet ExtraDDX? řádky a postup, formuláře

> ExtraDDX?=*keys*; *vb-keys*; *prompt*; *type*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

kde? číslo 1 - *n* určující, jaký typ DDX v seznamu, který definuje.

Každé pole je oddělené znakem ";". Pole a jejich účel jsou popsané níže.

- *keys*

  Seznam jednotlivých znaků určující, pro který dialog řídí tento typ proměnné je povolený.

  |Znak|Povolené ovládacího prvku|
  |-|-|
  E | Upravit
  C | dvoustavový zaškrtávací políčko
  c | TRI stav zaškrtávací políčko
  R | první přepínací tlačítko ve skupině
  L | pole se seznamem nonsorted
  l | seřazený seznam
  M | pole se seznamem (s upravovaná položka)
  N | nonsorted rozevíracího seznamu
  n | seřazené rozevíracího seznamu
  1 | Pokud vložení DDX měla být přidána do hlavní seznam (výchozí je přidat do funkce tail) obecně používá se pro rutiny DDX přenos vlastnost 'Control'.

- *vb-keys*

  Toto pole se používá pouze v rámci produktu 16 bitů pro ovládací prvky VBX (ovládací prvky VBX nejsou podporovány v produktu 32 bitů)

- *prompt*

  Řetězec, který se umístí v poli se seznamem vlastností (žádné uvozovky)

- *type*

  Jeden identifikátor pro typ generoval v hlavičkovém souboru. V našem příkladu s DDX_Time to se nastavuje na CTime.

- *vb-keys*

  Nepoužívá se v této verzi a by měla být prázdná

- *initValue*

  Počáteční hodnota – 0 nebo prázdné. Pokud je pole prázdné, bude žádné inicializačního řádku napsané v části //{{AFX_DATA_INIT implementační soubor. Prázdná položka by měla sloužit pro objekty jazyka C++ (například `CString`, `CTime`, a tak dále), které mají konstruktory, které zajistit správné inicializace.

- *DDX_Proc*

  Jeden identifikátor pro proceduru DDX_. C++ Název funkce musí začínat znakem "DDX_", ale neobsahují "DDX_" v \<DDX_Proc > identifikátor. V příkladu výše \<DDX_Proc > identifikátor bude čas. Když ClassWizard zapíše volání funkce v souboru implementace {{oddíl AFX_DATA_MAP přidá tento název k DDX_, tedy přicházejících u DDX_Time.

- *Komentář*

  Komentář se má zobrazit v dialogovém okně pro proměnnou s této DDX. Umístěte vás tady a obvykle poskytují něco jakýkoli text, který popisuje operace, která provádí DDX/DDV pár.

- *DDV_Proc*

  DDV část položka je volitelná. Ne všechny rutiny DDX mít odpovídající DDV rutiny. Často je pohodlnější zahrnout fázi ověřování jako nedílné součásti přenosu. To platí často při vaší rutinu DDV nevyžaduje žádné parametry, protože ClassWizard nepodporuje rutiny DDV bez parametrů.

- *arg*

  Jeden identifikátor DDV_ postup. C++ Název funkce musí začínat znakem "DDV_", ale nezahrnete "DDX_" \<DDX_Proc > identifikátor.

  *arg* následuje args DDV 1 nebo 2:

   - *promptN*

      Řetězec umístit nad upravit položku (& pro akcelerátor).

   - *fmtN*

      Znak formátu pro typ arg, jeden z:

      |Znak|Type|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | Long int (to znamená, long)|
      |U | Long bez znaménka (DWORD)|
      |f | float|
      |F | double|
      |s | odkazy řetězců|

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
