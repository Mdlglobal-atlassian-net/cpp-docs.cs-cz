---
title: Rozšiřující knihovny DLL
ms.date: 05/06/2019
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220774"
---
# <a name="mfc-extension-dlls"></a>Rozšiřující knihovny MFC DLL

Rozšiřující knihovna MFC DLL je knihovna DLL, která obvykle implementuje opakovaně použitelné třídy odvozené z existujících tříd knihovna Microsoft Foundation Class.

Rozšiřující knihovna MFC DLL má následující funkce a požadavky:

- Spustitelný soubor klienta musí být aplikace MFC kompilována s `_AFXDLL` definovaným.

- Knihovnu DLL rozšíření knihovny MFC lze také použít v běžné knihovně MFC DLL, která je dynamicky propojena s knihovnou MFC.

- Knihovny DLL rozšíření knihovny MFC by měly `_AFXEXT` být kompilovány s definovanými. Toto vynutí `_AFXDLL` také definovat a zajistit, aby byly správné deklarace získány ze souborů hlaviček knihovny MFC. Také zajišťuje, že `AFX_EXT_CLASS` je definován jako `__declspec(dllexport)` při vytváření knihovny DLL, což je nezbytné v případě, že toto makro používáte k deklaraci tříd v rozšiřující knihovně MFC DLL.

- Knihovny DLL rozšíření MFC by neměly vytvářet instance třídy odvozené z `CWinApp`, ale měly by spoléhat na klientskou aplikaci (nebo knihovnu DLL) k poskytnutí tohoto objektu.

- Knihovny DLL rozšíření knihovny MFC by však měly poskytovat `DllMain` funkci a provést jakoukoli nezbytnou inicializaci.

Rozšiřující knihovny DLL jsou sestaveny pomocí verze knihovny MFC s dynamickou knihovnou (také označované jako sdílená verze knihovny MFC). Knihovny DLL rozšíření MFC mohou používat pouze spustitelné soubory knihovny MFC (buď aplikace nebo běžné knihovny MFC DLL), které jsou vytvořeny pomocí sdílené verze knihovny MFC. Klientská aplikace i rozšiřující knihovna DLL knihovny MFC musí používat stejnou verzi MFCx0. dll. Pomocí knihovny DLL rozšíření knihovny MFC můžete odvodit nové vlastní třídy z knihovny MFC a následně nabízet tuto rozšířenou verzi knihovny MFC aplikacím, které volají vaši DLL knihovnu.

Rozšiřující knihovny DLL lze také použít pro předávání objektů odvozených od knihovny MFC mezi aplikací a knihovnou DLL. Členské funkce přidružené k předanému objektu existují v modulu, ve kterém byl objekt vytvořen. Vzhledem k tomu, že tyto funkce jsou správně exportovány při použití sdílené knihovny DLL verze knihovny MFC, je možné volně předat ukazatele objektů MFC nebo MFC odvozené od aplikace a rozšiřujících knihoven DLL MFC, které načte.

Rozšiřující knihovna MFC DLL používá sdílenou verzi knihovny MFC stejným způsobem jako aplikace používá sdílenou verzi knihovny MFC DLL, s několika dalšími požadavky:

- `CWinApp`Neobsahuje objekt odvozený od. Musí fungovat s `CWinApp`objektem odvozeným od klientské aplikace. To znamená, že aplikace klienta vlastní hlavní pumpu zpráv, nečinný cyklus atd.

- Volá `AfxInitExtensionModule` jeho `DllMain` funkci. Měla by být zaškrtnuta návratová hodnota této funkce. Pokud je vrácena nulová hodnota z `AfxInitExtensionModule`, vrátí 0 z vaší `DllMain` funkce.

- Vytvoří objekt **CDynLinkLibrary** během inicializace, pokud knihovna DLL rozšíření MFC chce exportovat `CRuntimeClass` objekty nebo prostředky do aplikace.

Před verzí 4,0 knihovny MFC byl tento typ knihovny DLL volán jako AFXDLL –. AFXDLL – odkazuje na `_AFXDLL` symbol preprocesoru, který je definován při sestavování knihovny DLL.

Knihovny importu pro sdílenou verzi knihovny MFC jsou pojmenovány podle konvence popsaných v tématu zásady [vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual Studio poskytuje předem připravené verze knihoven MFC DLL a navíc několik knihoven DLL, které nepatří do knihovny MFC, které lze použít a distribuovat s vašimi aplikacemi. Ty jsou popsány v balíčku Redist. txt, který je nainstalován do složky Program Files\Microsoft Visual Studio.

Pokud exportujete pomocí souboru. def, umístěte následující kód na začátek a konec hlavičkového souboru:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Tyto čtyři řádky zajišťují, že je váš kód správně kompilován pro rozšiřující knihovnu MFC DLL. Vynechávání těchto čtyř řádků může způsobit, že vaše knihovna DLL buď nebude správně zkompilována nebo bude propojena.

Pokud potřebujete předat ukazatel na objekt MFC nebo odvozený od knihovny MFC do nebo z knihovny MFC DLL, knihovna DLL by měla být knihovnou DLL rozšíření MFC. Členské funkce přidružené k předanému objektu existují v modulu, ve kterém byl objekt vytvořen. Vzhledem k tomu, že tyto funkce jsou správně exportovány při použití sdílené knihovny DLL verze knihovny MFC, je možné volně předat ukazatele objektů MFC nebo MFC odvozené od aplikace a rozšiřujících knihoven DLL MFC, které načte.

Z důvodu problémů s popsáním a exportem názvů C++ může být seznam exportu z knihovny DLL rozšíření MFC odlišný od ladicích a maloobchodních verzí stejné knihovny DLL a knihoven DLL pro různé platformy. Maloobchodní MFCx0. dll má přibližně 2 000 exportovaných vstupních bodů; MFCx0D ladění. dll má přibližně 3 000 exportovaných vstupních bodů.

## <a name="memory-management"></a>Správa paměti

MFCx0. dll a všechny rozšiřující knihovny MFC, které jsou načteny do adresního prostoru klientské aplikace, používají stejné přidělování paměti, načítání prostředků a další globální stavy knihovny MFC, jako kdyby byly ve stejné aplikaci. To je důležité, protože knihovny knihoven DLL, které nejsou knihovny MFC, a běžné knihovny MFC DLL mají přesný opak a mají každou knihovnu DLL, která přiděluje vlastní fond paměti.

Pokud knihovna DLL rozšíření MFC přiděluje paměť, může být tato paměť volně intermixa s jakýmkoli jiným objektem přiděleným aplikacím. Kromě toho, pokud aplikace, která dynamicky propojuje k knihovně MFC, neproběhne úspěšně, ochrana operačního systému udržuje integritu jakékoli jiné aplikace MFC sdílející knihovnu DLL.

Podobně ostatní globální stavy MFC, jako je aktuální spustitelný soubor pro načtení prostředků z nástroje, jsou sdíleny také mezi klientskou aplikací a všemi rozšiřujícími knihovnami MFC a také MFCx0. dll.

## <a name="sharing-resources-and-classes"></a>Sdílení prostředků a tříd

Export prostředků se provádí prostřednictvím seznamu prostředků. Každá aplikace obsahuje jednotlivě propojený seznam objektů **CDynLinkLibrary** . Při hledání prostředku většina standardních implementací knihovny MFC, které načítají prostředky, vypadají jako první v aktuálním modulu prostředků (`AfxGetResourceHandle`) a pokud se prostředek nenajde, Projděte si seznam objektů **CDynLinkLibrary** , které se pokoušejí načíst požadovaný prostředek.

Procházení seznamu má nevýhodu, že je trochu pomalejší a vyžaduje správu rozsahů ID prostředků. Má výhodu, že klientská aplikace, která odkazuje na několik rozšiřujících knihoven DLL knihovny MFC, může použít jakýkoli prostředek poskytnutý knihovnou DLL bez nutnosti zadat popisovač instance knihovny DLL. `AfxFindResourceHandle`je rozhraní API, které se používá k procházení seznamu prostředků pro vyhledání dané shody. Převezme název a typ prostředku a vrátí popisovač prostředku, kde byl poprvé nalezen (nebo NULL).

Pokud nechcete procházet seznam a načíst pouze prostředky z konkrétního místa, použijte funkce `AfxGetResourceHandle` a `AfxSetResourceHandle` uložte původní popisovač a nastavte nový popisovač. Před návratem do klientské aplikace Nezapomeňte obnovit původní popisovač prostředku. Příklad použití tohoto přístupu pro explicitní načtení nabídky naleznete v tématu Testdll2. cpp v ukázce knihovny MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

Dynamické vytváření objektů knihovny MFC s názvem knihovny MFC je podobné. Mechanismus deserializace objektů knihovny MFC musí mít všechny registrované `CRuntimeClass` objekty, aby je bylo možné rekonstruovat dynamickým vytvářením objektů C++ požadovaného typu na základě toho, co bylo dříve uloženo.

V případě ukázkového [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)knihovny MFC vypadá seznam přibližně takto:

```
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE
               |                      |
          TESTDLL2.DLL           TESTDLL2.DLL
               |                      |
          TESTDLL1.DLL           TESTDLL1.DLL
               |                      |
           MFCOxxD.DLL                |
               |                      |
           MFCDxxD.DLL                |
               |                      |
            MFCxxD.DLL            MFCxx.DLL
```

kde *XX* je číslo verze; například 42 představuje verzi 4,2.

MFCxx. dll je obvykle poslední v seznamu prostředků a tříd. MFCxx. dll zahrnuje všechny standardní prostředky knihovny MFC, včetně řetězců s výzvou pro všechna standardní ID příkazů. Umístění na konci seznamu umožňuje knihovnám dll a klientským aplikacím, aby nemusely mít vlastní kopii standardních prostředků knihovny MFC, ale aby se místo toho spoléhaly na sdílené prostředky v souboru MFCxx. dll.

Sloučení prostředků a názvů tříd všech knihoven DLL do oboru názvů klientské aplikace je nevýhodou, abyste měli pozor na to, co si vybíráte podle ID nebo názvů.

Ukázka [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) spravuje obor názvů sdíleného prostředku pomocí více souborů hlaviček.

Pokud vaše knihovna DLL rozšíření MFC potřebuje zachovat další data pro každou aplikaci, můžete odvodit novou třídu z programu **CDynLinkLibrary** a vytvořit ji v `DllMain`. Při spuštění může knihovna DLL vyhledat v seznamu objektů **CDynLinkLibrary** aktuální aplikace, aby nalezla jednu pro danou knihovnu DLL rozšíření MFC.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializace knihovny DLL rozšíření MFC](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Tipy k používání sdílených souborů prostředků](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)

- [Běžné knihovny MFC DLL staticky propojené s knihovnou MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
