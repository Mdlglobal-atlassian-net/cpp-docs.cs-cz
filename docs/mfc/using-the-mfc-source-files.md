---
title: Použití zdrojových souborů MFC
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ca5799da7a6ada42db20e3551b3fb7262e8990a0
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631669"
---
# <a name="using-the-mfc-source-files"></a>Použití zdrojových souborů MFC

Knihovna Microsoft Foundation Class (MFC) poskytuje úplný zdrojový kód. Soubory hlaviček (. h) jsou v adresáři *\atlmfc\include* . Implementační soubory (. cpp) jsou v adresáři *\atlmfc\src\mfc* .

Tento článek vysvětluje konvence, které knihovna MFC používá ke komentování různých částí každé třídy, co tyto komentáře znamenají a co byste měli očekávat v každé části. Průvodci sady Visual Studio používají podobné konvence pro třídy, které pro vás vytvoří, a tyto konvence pravděpodobně budete užitečné pro vlastní kód.

Můžete znát klíčová slova **Public**, **Protected**a **Private** C++ . V hlavičkových souborech knihovny MFC najdete každou třídu, která může mít několik z nich. Například veřejné proměnné členů a funkce mohou být ve více než jednom klíčovém slově **Public** . Je to proto, že knihovna MFC odděluje členské proměnné a funkce na základě jejich použití, nikoli podle typu povoleného přístupu. MFC používá **soukromě** . Dokonce i položky považované za podrobnosti oimplementaci jsou často chráněny a mnohokrát jsou **veřejné**. I když se přístup k podrobnostem implementace nedoporučuje, knihovna MFC toto rozhodnutí ponechá.

Ve zdrojových souborech knihovny MFC a hlavičkových souborech, které Průvodce aplikací MFC vytvoří, najdete v deklaracích třídy komentáře, jako jsou ty, které jsou v deklaracích tříd (obvykle v tomto pořadí):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a>Příklad komentářů

Následující částečný výpis třídy `CStdioFile` používá většinu standardních komentářů, které knihovna MFC využívá ve svých třídách k rozdělení členů třídy podle způsobů jejich použití:

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

Tyto komentáře konzistentně označují oddíly deklarace třídy, které obsahují podobné druhy členů třídy. Mějte na paměti, že jsou to konvence knihovny MFC, nikoli nastavená pravidla.

## <a name="-constructors-comment"></a>Komentář k konstruktorům

Oddíl deklarace třídy knihovny MFC deklaruje konstruktory (v tomto C++ smyslu) a všechny inicializační funkce vyžadované pro skutečně použití objektu. `// Constructors` Například `CWnd::Create` je v sekci konstruktory, protože před `CWnd` použitím objektu musí být "plně konstruován", a to nejdříve voláním C++ konstruktoru a voláním `Create` funkce. Obvykle jsou tito členové veřejné.

Třída `CStdioFile` má například pět konstruktorů, z nichž jeden je zobrazen v seznamu pod [příkladem komentářů](#an-example-of-the-comments).

## <a name="-attributes-comment"></a>Komentář k atributům

`// Attributes` Oddíl deklarace třídy knihovny MFC obsahuje veřejné atributy (nebo vlastnosti) objektu. Obvykle jsou atributy členské proměnné nebo funkce Get/Set. Funkce Get a set mohou být nebo nemusí být virtuální. Funkce Get jsou často const,protože ve většině případů nemají vedlejší účinky. Tyto členy jsou obvykle veřejné. Chráněné a privátní atributy se obvykle nacházejí v části implementace.

V ukázkovém výpisu ze `CStdioFile`třídy v rámci [příkladu komentáře](#an-example-of-the-comments)obsahuje seznam jednu členskou proměnnou *m_pStream*. Třída `CDC` vypisuje do tohoto komentáře téměř 20 členů.

> [!NOTE]
> Velké třídy, jako `CDC` jsou a `CWnd`, mohou mít tolik členů, kteří jednoduše vypíše všechny atributy v jedné skupině, takže nebudete mnohem přehlednější. V takových případech knihovna tříd používá jiné komentáře jako záhlaví k dalšímu vymezení členů. Například `CDC` používá `// Device-Context Functions`, ,adalší`// Drawing Attribute Functions`. `// Drawing Tool Functions` Skupiny, které reprezentují atributy, budou následovat po běžné syntaxi popsané výše. Mnoho tříd OLE má takzvaný `// Interface Maps`oddíl implementace.

## <a name="-operations-comment"></a>Komentář k operacím

`// Operations` Oddíl deklarace třídy knihovny MFC obsahuje členské funkce, které lze volat na objekt, aby se prováděly věci nebo prováděly akce (provádět operace). Tyto funkce jsou obvykle nekonstantní , protože mají obvykle vedlejší účinky. Můžou být virtuální nebo nevirtuální v závislosti na potřebách třídy. Obvykle jsou tito členové veřejné.

V ukázkovém výpisu z `CStdioFile`třídy, v [příkladu komentáře](#an-example-of-the-comments), obsahuje seznam tři členské funkce v rámci tohoto komentáře: `WriteString` a dvě přetížení. `ReadString`

Stejně jako u atributů mohou být operace dále rozděleny.

## <a name="-overridables-comment"></a>K přepisovatelným komentář

`// Overridables` Oddíl deklarace třídy knihovny MFC obsahuje virtuální funkce, které lze přepsat v odvozené třídě, pokud potřebujete změnit chování základní třídy. Obvykle se nazývají začínající znakem "on", i když není nezbytně nutné. Funkce jsou určeny k přepsání a často implementují nebo poskytují nějaký druh "zpětného volání" nebo "Hooku". Obvykle jsou tito členové chráněni.

V samotné knihovně MFC jsou čistě virtuální funkce vždy umístěny v této části. Čistě virtuální funkce v C++ nástroji má podobu:

`virtual void OnDraw( ) = 0;`

V ukázkovém výpisu z `CStdioFile`třídy, v [příkladu komentáře](#an-example-of-the-comments), seznam neobsahuje žádné k přepisovatelným oddíly. Třída `CDocument`na druhé straně obsahuje přibližně 10 přepisovatelných členských funkcí.

V některých třídách lze také zobrazit komentář `// Advanced Overridables`. Tyto funkce jsou ty, které by se měly pokusit přepsat jenom pokročilí programátoři. Pravděpodobně je nikdy nebudete muset potlačit.

> [!NOTE]
> Konvence popsané v tomto článku také dobře spolupracují, pro metody automatizace (dříve označované jako automatizace OLE) a vlastnosti. Metody automatizace jsou podobné operacím MFC. Vlastnosti služby Automation jsou podobné atributům knihovny MFC. Události automatizace (podporované pro ovládací prvky ActiveX, dříve označované jako ovládací prvky OLE) jsou podobné prvkům, které lze přepsat, jako členské funkce v knihovně MFC.

## <a name="-implementation-comment"></a>Implementační komentář

`// Implementation` Oddíl je nejdůležitější součástí libovolné deklarace třídy MFC.

V této části najdete všechny podrobnosti o implementaci. V této části se můžou objevit jak členské proměnné, tak členské funkce. Vše pod tímto řádkem se může v budoucí verzi knihovny MFC změnit. Pokud se nemůžete vyhnout, neměli byste spoléhat na podrobnosti pod `// Implementation` řádkem. Kromě toho jsou nedokumentované členy deklarované pod implementačním řádkem, i když je některá implementace popsána v technických poznámkách. Přepsání virtuálních funkcí v základní třídě se nachází v této části bez ohledu na to, v jaké části je funkce základní třídy definována. Když funkce přepisuje implementaci základní třídy, je považována za detaily implementace. Obvykle jsou tito členové chráněni, ale ne vždy.

`// Implementation` [](#an-example-of-the-comments)V seznamu pod příkladem komentářů mohou být členy deklarované pod komentářem deklarovány jako veřejné, chráněné nebo soukromé. `CStdioFile` Tyto členy používejte jenom opatrně, protože se můžou v budoucnu změnit. Deklarování skupiny členů jako **veřejné** může být nezbytné, aby implementace knihovny tříd fungovala správně. Neznamená to však, že můžete bezpečně použít členy, které jsou deklarovány.

> [!NOTE]
> Komentáře zbývajících typů můžete najít buď výše, nebo pod `// Implementation` komentářem. V obou případech popisují typy členů deklarovaných níže. Pokud k nim dojde pod `// Implementation` komentářem, měli byste předpokládat, že se členové mohou v budoucích verzích knihovny MFC měnit.

## <a name="see-also"></a>Viz také:

[Obecná témata MFC](../mfc/general-mfc-topics.md)
