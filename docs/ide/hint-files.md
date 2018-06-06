---
title: Pomocného parametru soubory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- cpp.hint
- vc.hint.file
dev_langs:
- C++
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 687e5cba94693a752f934d7816e6a7c36e318354
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33336694"
---
# <a name="hint-files"></a>Soubory pokynů
A *soubor pokynů* pomáhá sady Visual Studio integrované vývojové prostředí (IDE) interpretovat identifikátory Visual C++, jako jsou názvy funkcemi a makry. Když otevřete projektu Visual C++, rozhraní IDE *systém analýzy* analyzuje kód do každého souboru zdroje v projektu a shromažďuje informace o každém identifikátoru. Prostředí IDE použije tyto informace k podpoře funkce, jako **zobrazení tříd** prohlížeče a **navigační panel**.  
  
 Systém analýzy, který je uveden v Visual C++ 2010, rozumí syntaxi C/C++, ale může špatně interpretovat výraz, který obsahuje makra. Příkaz může dojít k nesprávné interpretaci Pokud makro způsobí, že zdrojový kód syntakticky nesprávná, protože do něj zapisuje. Příkaz se může stát syntakticky správný při kompilaci zdrojového kódu a preprocesorem [makro identifikátor](../preprocessor/hash-define-directive-c-cpp.md) s jeho definice. Systém analýzy funguje bez nutnosti sestavení projektu, protože používá soubory pokynů interpretovat makra. Proto procházení funkce, jako například **zobrazení tříd** je ihned k dispozici.  
  
 Soubor pokynů obsahuje uživatelsky přizpůsobitelné *pomocné parametry*, které mají stejnou syntaxi jako definice maker jazyka C/C++. Visual C++ zahrnuje integrovanou pomocný parametr souboru, který je vhodný pro většinu projektů, ale můžete vytvořit vlastní soubory pokynů ke zlepšení způsobu, jakým Visual Studio zpracovává identifikátory.  
  
> [!IMPORTANT]
>  Pokud změníte nebo přidáte soubor pokynů, je nutné odstranit soubor SDF nebo VC.db souboru v řešení, aby změny vstoupily v platnost.  
  
## <a name="scenario"></a>Scénář  
 Předpokládejme, že následující kód je v zdrojový soubor, který zkoumáte **zobrazení tříd** prohlížeče. `STDMETHOD` Makro deklaruje metodu s názvem `myMethod` které přijímá jeden parametr a vrací ukazatel na **HRESULT**.  
  
```  
// Source code file.  
STDMETHOD(myMethod)(int parameter1);  
```  
  
 Následující definice maker jsou v samostatném hlavičkovém souboru.  
  
```  
// Header file.  
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)  
#define STDMETHODCALLTYPE __stdcall  
#define HRESULT void*  
```  
  
 Systém analýzy nemůže interpretovat ve zdrojovém kódu, protože funkce pojmenovaná STDMETHOD se zdá být deklarována a že prohlášení nemá správnou syntaxi, protože obsahuje dva seznamy parametrů. Systém analýzy neotevře soubor hlaviček, aby zjistil definice pro `STDMETHOD`, `STDMETHODCALLTYPE`, a `HRESULT` makra. Protože systém analýzy nemůže interpretovat `STDMETHOD` makro, ignoruje celý výraz a pokračuje v analýze.  
  
 Systém analýzy nepoužívá soubory hlaviček, protože projekt může záviset na jeden nebo více důležitých souborů hlaviček. Pokud se změní všechny hlavičkový soubor, systém analýzy možná muset prozkoumat všechny soubory hlaviček v projektu, což zpomalí výkon rozhraní IDE. Místo toho využívá systém analýzy pokyny, které určují způsob zpracování `STDMETHOD`, `STDMETHODCALLTYPE`, a `HRESULT` makra.  
  
 Jak poznáte, že potřebujete nápovědu? A pokud potřebujete nápovědu, jaký typ měli byste vytvořit? Jeden znak, je potřeba nápovědu je-li zobrazení identifikátoru v **zobrazení tříd** není konzistentní s zobrazení v **Editor**. Například **zobrazení tříd** může není zobrazení člena třídy, které znáte existuje nebo je nesprávný název člena. Další informace o typech pokynů, které řeší běžné problémy najdete v části co makra vyžadují A pomocný parametr? části dále v tomto tématu.  
  
## <a name="architecture"></a>Architektura  
 Soubory pokynů náleží do fyzického adresáře, ne do logických adresářů znázorněný v **Průzkumníku řešení**. Nemáte soubor pokynů přidejte do projektu soubor pokynů mít vliv. Systém analýzy používá soubory pokynů pouze v případě, že analyzuje zdrojové soubory.  
  
 Každý soubor pokynů je pojmenován **cpp.hint**. Proto může obsahovat soubor pokynů, ale pouze jeden pomocný parametr souboru se může objevit v jednom adresáři.  
  
 Soubory pokynů nula nebo více můžou mít vliv projektu. Pokud nejsou žádné soubory pokynů, používá systém analýzy chyby obnovení techniky ignorovat nečitelné zdrojového kódu. Systém analýzy, jinak používá následující strategie k hledání a získání pokynů.  
  
### <a name="search-order"></a>Pořadí hledání  
 Systém analýzy vyhledá adresářů pro soubory pokynů v následujícím pořadí.  
  
-   Adresář, který obsahuje instalační balíček pro Visual C++ (**vcpackages**). Tento adresář obsahuje soubor předdefinovaných pomocný parametr, který popisuje symboly v často používaných systémové soubory, například **odkazující na Windows**. V důsledku toho projekt automaticky zdědí většinu pokynů, které potřebuje.  
  
-   Cestu z kořenového adresáře zdrojového souboru do adresáře, který obsahuje zdrojový soubor sám sebe. V typickém projektu Visual C++ kořenový adresář obsahuje soubor řešení nebo produktu project.  
  
     Výjimka, která má toto pravidlo je-li *stop soubor* v cestě ke zdrojovému souboru. Stop soubor poskytuje další kontrolu nad pořadí hledání a je libovolný soubor s názvem **cpp.stop**. Namísto spuštění z kořenového adresáře, vyhledává systém analýzy z adresáře, který obsahuje stop soubor do adresáře, který obsahuje zdrojový soubor. V typickém projektu není nutné stop soubor.  
  
### <a name="hint-gathering"></a>Pomocný parametr shromažďování  
 Soubor pokynů obsahuje nula nebo více *pomocné parametry*. Nápovědu je definované nebo odstranit stejně jako makra jazyka C/C++. To znamená `#define` direktivy preprocesoru vytvoří nebo znovu definuje nápovědu a `#undef` pokyn odstraní.  
  
 Systém analýzy otevře každý soubor pokynů v pořadí vyhledávání popsané výše, shromažďuje pokyny v každém souboru do sady *efektivní pokyny*a pak používá efektivní pokyny k interpretaci identifikátorů v kódu.  
  
 Systém analýzy používá následující pravidla pro shromáždění pokynů.  
  
-   Pokud nový pokyn určuje název, který již není definován, přidá nový pokyn název efektivní pokyny.  
  
-   Pokud nový pokyn určuje název, který je již definován, přináší nový pokyn existující pokyn.  
  
-   Pokud je nový pokyn `#undef` direktivy, který určuje existující efektivní pokyn, nový pokyn odstraní existující pokyn.  
  
 První pravidlo znamená, že efektivní pokyny dědí z dříve otevřených souborů pokynů. Poslední dvě pravidla znamenají, že pomocné parametry, které později v pořadí hledání můžete přepsat dřívější pokyny. Například můžete přepsat jakékoliv předchozí pokyny, když vytvoříte soubor pokynů v adresáři, který obsahuje zdrojový soubor.  
  
 Popis shromažďování pomocných parametrů najdete v článku `Example` později v tomto tématu.  
  
### <a name="syntax"></a>Syntaxe  
 Pomocné parametry jsou vytvořeny a odstranit se stejnou syntaxí, jako preprocesoru, které vytvářet a odstraňovat makra. Ve skutečnosti využívá systém analýzy preprocesoru jazyka C/C++ pro vyhodnocení těchto pokynů. Další informace o preprocesor – direktivy najdete v tématu [#define – direktiva (C/C++)](../preprocessor/hash-define-directive-c-cpp.md) a [#undef – direktiva (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md).  
  
 Prvky pouze neobvyklou syntaxe jsou `@<`, `@=`, a `@>` náhradní řetězce. Jedná se o řetězce nahrazení specifické pro soubor, které se používají pouze s *mapy* makra. Mapu je sada maker, které se vztahují data, funkce nebo události další data, funkce nebo obslužné rutiny událostí. Například `MFC` používá k vytvoření mapy [zprávy mapy](../mfc/reference/message-maps-mfc.md), a `ATL` používá k vytvoření mapy [objektu mapy](../atl/reference/object-map-macros.md). Řetězce nahrazení specifické pro soubor znamenat počáteční, zprostředkující a koncovou elementy mapy. Je důležité pouze název makra mapy. Proto každý řetězec nahrazení záměrně skryje implementaci makra.  
  
 Pomocné parametry použijte následující syntaxi.  
  
|Syntaxe|Význam|  
|------------|-------------|  
|`#define` *pomocný parametr name* *řetězec nahrazení*<br /><br /> `#define` *pomocný parametr name* `(` *parametr*,... `)` *řetězec nahrazení*|Direktiva preprocesoru, která definuje nový pokyn nebo znovu definuje existující pokyn. Po – direktiva, preprocesor nahradí všechny výskyty *pomocný parametr name* ve zdrojovém kódu s *řetězec nahrazení*.<br /><br /> Druhý formulář syntaxe definuje funkce jako nápovědu. V případě funkce jako nápovědu ve zdrojovém kódu preprocesor nejprve nahradí všechny výskyty *parametr* v *řetězec nahrazení* s argumentem odpovídající zdrojový kód a potom nahradí *pomocný parametr name* s *řetězec nahrazení*.|  
|`@<`|Pro soubor konkrétní *řetězec nahrazení* určující spuštění sady elementů mapy.|  
|`@=`|Pro soubor konkrétní *řetězec nahrazení* určující vložený prvek mapy. Mapa může mít víc elementů mapy.|  
|`@>`|Pro soubor konkrétní *řetězec nahrazení* určující konce sady elementů mapy.|  
|`#undef` *pomocný parametr name*|Preprocesor – direktiva, které odstraní existující pokyn. Název v pomocném parametru poskytuje *pomocný parametr name* identifikátor.|  
|`//` *Komentář*|Komentář jeden řádek.|  
|`/*` *Komentář* `*/`|Víceřádkový komentář.|  
  
## <a name="what-macros-require-a-hint"></a>Co makra vyžadují nápovědu?  
 Některé typy makra může narušovat systém analýzy. Tato část popisuje typy makra, které mohly by způsobit problém a typ pomocného parametru, že můžete vytvořit pro řešení tohoto problému.  
  
### <a name="disruptive-macros"></a>Rušivé makra  
 Některé makra způsobit, že systém analýzy špatně interpretuje zdrojový kód, ale můžete ignorovat bez zhoršení možnosti procházení. Například jazyk poznámky zdrojového kódu ([SAL](../c-runtime-library/sal-annotations.md)) makra odkazující na atributy C++, které vám pomůžou najít programovací chyby. Pokud chcete ignorovat poznámky SAL při procházení kódu, můžete chtít vytvořit soubor pomocný parametr, který poznámky skryje.  
  
 V následující zdrojový kód, zadejte parametr pro `FormatWindowClassName()` funkce je `PXSTR`, a název parametru je `szBuffer`. Ale analýza chyb systému `_Pre_notnull_` a `_Post_z_` SAL – poznámky pro parametr typu nebo název parametru.  
  
 **Zdrojový kód:**  
  
```  
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)  
```  
  
 **Strategie:** Null definice  
  
 Strategie v této situaci se zachází poznámek SAL, jako kdyby neexistuje. Chcete-li to provést, zadejte pokyn, jehož řetězec nahrazení je null. V důsledku toho systém analýzy ignoruje poznámky a **zobrazení tříd** prohlížeče je nezobrazí. (Visual C++ zahrnuje integrovanou pomocný parametr souboru, který skryje poznámky SAL.)  
  
 **Soubor pokynů:**  
  
```  
#define _Pre_notnull_  
```  
  
### <a name="concealed-cc-language-elements"></a>Jazykové elementy skryté C/C++  
 Typický případ, že systém analýzy špatně interpretuje zdrojový kód je makro, které skryje C/C++ [interpunkci](../cpp/punctuators-cpp.md) nebo [– klíčové slovo](../cpp/keywords-cpp.md) tokenu. To znamená, makro může obsahovat polovinu pár interpunkční znaky, jako `<>`, `[]`, `{}`, a `()`.  
  
 V následující zdrojový kód `START_NAMESPACE` makro skryje nepárové levém levá složená závorka (`{`).  
  
 **Zdrojový kód:**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
 **Strategie:** přímé kopírování  
  
 Pokud sémantiku makra jsou důležité pro možnosti procházení, vytvořte pomocný parametr, který je stejný jako makro. Systém analýzy přeloží makro do definice v souboru nápovědy.  
  
 Poznámka: Pokud makro ve zdrojovém souboru obsahuje jiné makra, tyto makra interpretaci pouze v případě, že jsou již v sadě efektivní pokyny.  
  
 **Soubor pokynů:**  
  
```  
#define START_NAMESPACE namespace MyProject {  
```  
  
### <a name="maps"></a>Mapy  
 Mapu se skládá z maker, která určí počáteční element, koncový element a nula nebo více zprostředkující prvků. Systém analýzy interpretuje mapu špatně, protože každé makro mapy skryje elementy jazyka C/C++ a syntaxe dokončení příkazu C/C++ je distribuován do mnoha samostatné makra.  
  
 Definuje následující zdrojový kód `BEGIN_CATEGORY_MAP`, `IMPLEMENTED_CATEGORY`, a `END_CATEGORY_MAP` makra.  
  
 **Zdrojový kód:**  
  
```  
#define BEGIN_CATEGORY_MAP(x)\  
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\  
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {  
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },  
#define END_CATEGORY_MAP()\  
   { _ATL_CATMAP_ENTRY_END, NULL } };\  
   return( pMap ); }  
```  
  
 **Strategie:** identifikace elementů mapy  
  
 Zadejte pomocné parametry pro spuštění, střední (pokud existuje) a end elementy mapy. Použít speciální mapové řetězce nahrazení `@<`, `@=`, a `@>`. Další informace najdete v tématu `Syntax` v tomto tématu.  
  
 **Soubor pokynů:**  
  
```  
// Start of the map.  
#define BEGIN_CATEGORY_MAP(x) @<  
// Intermediate map element.  
#define IMPLEMENTED_CATEGORY( catid ) @=  
// Intermediate map element.  
#define REQUIRED_CATEGORY( catid ) @=  
// End of the map.  
#define END_CATEGORY_MAP() @>  
```  
  
### <a name="composite-macros"></a>Složené makra  
 Složené makra obsahují jeden nebo více typů makro, které matou systém analýzy.  
  
 Obsahuje následující zdrojový kód `START_NAMESPACE` makro, které určuje začátek oboru názvů, a `BEGIN_CATEGORY_MAP` makro, které určuje začátek mapy.  
  
 **Zdrojový kód:**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
 **Strategie:** přímé kopírování  
  
 Vytvoření odkazů pro `START_NAMESPACE` a `BEGIN_CATEGORY_MAP` makra a potom vytvořit pokyn pro `NSandMAP` makro, která je stejná, jako je uvedené výše pro zdrojový kód. Případně pokud složené makro obsahuje pouze rušivé makra a mezer, můžete definovat pokyn, jehož řetězec nahrazení je definici hodnotu null.  
  
 V tomto příkladu se předpokládá `START_NAMESPACE` již nápovědu, jak je popsáno v tomto tématu v `Concealed C/C++ Language Elements` podnadpisu. A předpokládají `BEGIN_CATEGORY_MAP` má nápovědu, jak je popsáno výše v `Maps`.  
  
 **Soubor pokynů:**  
  
```  
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP  
```  
  
### <a name="inconvenient-macros"></a>Nevyhovující makra  
 Některé makra lze interpretovat systémem analýzy, ale zdrojový kód je obtížné číst, protože je makro dlouhý nebo složitý. V zájmu přehlednosti můžete zadat nápovědu, která zjednodušuje zobrazení makra.  
  
 **Zdrojový kód:**  
  
```  
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)  
```  
  
 **Strategie:** zjednodušení  
  
 Vytvořte pomocný parametr, který zobrazuje jednoduchou definici makra.  
  
 **Soubor pokynů:**  
  
```  
#define STDMETHOD(methodName) void* methodName  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje, jak jsou shromážděna pomocné parametry z soubory pokynů. V tomto příkladu nejsou použity stop soubory.  
  
 Následující obrázek znázorňuje některé z fyzického adresáře v projektu jazyka Visual C++. Soubory pokynů jsou v `vcpackages`, `Debug`, `A1`, a `A2` adresáře.  
  
### <a name="hint-file-directories"></a>Pomocný parametr souborové adresáře  
 ![Běžné a projekt&#45;konkrétní pomocný parametr souborové adresáře. ] (../ide/media/hintfile.png "HintFile")  
  
### <a name="directories-and-hint-file-contents"></a>Adresářů a obsah souboru pokynů  
 V následujícím seznamu jsou adresáře v tomto projektu, které obsahují soubory pokynů a obsah těchto souborů pokynů. Jenom některé z mnoha pomocné parametry v `vcpackages` souboru pomocný parametr adresáře jsou uvedené.  
  
-   vcpackages  
  
    ```  
    // vcpackages (partial list)  
    #define _In_  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    ```  
  
-   Ladit  
  
    ```  
    // Debug  
    #undef _In_  
    #define OBRACE {  
    #define CBRACE }  
    #define RAISE_EXCEPTION(x) throw (x)  
    #define START_NAMESPACE namespace MyProject {  
    #define END_NAMESPACE }  
    ```  
  
-   A1  
  
    ```  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {  
    ```  
  
-   A2  
  
    ```  
    // A2  
    #undef OBRACE  
    #undef CBRACE  
    ```  
  
### <a name="effective-hints"></a>Efektivní pokyny  
 Následující tabulka uvádí efektivní pokyny pro zdrojové soubory v tomto projektu.  
  
-   Zdroj souboru: A1_A2_B.cpp  
  
-   Efektivní pokyny:  
  
    ```  
    // vcpackages (partial list)  
    #define _In_opt_  
    #define _In_z_  
    #define _In_opt_z_  
    #define _In_count_(size)  
    // Debug...  
    #define RAISE_EXCEPTION(x) throw (x)  
    // A1  
    #define START_NAMESPACE namespace A1Namespace {   
    // ...Debug  
    #define END_NAMESPACE }  
    ```  
  
 Následující poznámky platí pro v předchozím seznamu.  
  
-   Jsou efektivní pokyny z `vcpackages`, `Debug`, `A1`, a `A2` adresáře.  
  
-   **#Undef** direktivy v `Debug` odebrat soubor pokynů `#define _In_` pomocného parametru v `vcpackages` souboru pokynů v adresáři.  
  
-   Soubor pokynů v `A1` znovu definuje adresář `START_NAMESPACE`.  
  
-   `#undef` Pomocného parametru v `A2` odstranit adresář odkazů pro `OBRACE` a `CBRACE` v `Debug` souboru pokynů v adresáři.  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)    
 [#define – direktiva (C/C++)](../preprocessor/hash-define-directive-c-cpp.md)   
 [#undef – direktiva (C/C++)](../preprocessor/hash-undef-directive-c-cpp.md)   
 [SAL – poznámky](../c-runtime-library/sal-annotations.md)   
 [Mapy zpráv](../mfc/reference/message-maps-mfc.md)   
 [Makra Map zpráv](../atl/reference/message-map-macros-atl.md)   
 [Makra map objektů](../atl/reference/object-map-macros.md)