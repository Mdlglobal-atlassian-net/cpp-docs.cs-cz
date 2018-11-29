# <a name="contributing"></a>Přispívání

Děkujeme vám za váš zájem o přispívání do dokumentace k Visual C++.

V tomto tématu, zobrazí se vám základní proces přidávání nebo aktualizaci obsahu v [webu dokumentace jazyka Visual C++](https://docs.microsoft.com/cpp).

V tomto tématu se budeme zabývat:

* [Proces pro přispívání](#process-for-contributing)
* [Pro a proti](#dos-and-donts)
* [Vytváření webu docs](#building-the-docs)
* [Přispívání do vzorků](#contributing-to-samples)
* [Přispěvatel licenční smlouvy](#contributor-license-agreement)

## <a name="process-for-contributing"></a>Proces pro přispívání

**Krok 1:** otevřete problém s popisem článku chcete zapsat a toho, jak souvisí stávajícího obsahu.
Obsah uvnitř **dokumentace** složky je uspořádaný do oddílů, které jsou uspořádány podle oblasti obsahu (například ladicí program). Pokusí se určit správnou složku pro nový obsah. Získáte zpětnou vazbu na váš návrh.

Přeskočit tento první krok pro malé změny.

**Krok 2:** Forku `MicrosoftDocs/cpp-docs` úložiště.

**Krok 3:** vytvořit `branch` svůj článek.

**Krok 4:** napište svůj článek.

Pokud je nové téma, můžete to [soubor šablony](./styleguide/template.md) jako výchozí bod. Obsahuje pokyny pro zápis a také vysvětluje metadat, vyžaduje se pro každý článek, jako je například informace o autorovi.

Přejděte do složky, která odpovídá umístění obsahu pro váš článek v kroku 1.
Tato složka obsahuje soubory Markdown pro všechny články v této části. V případě potřeby vytvořte novou složku pro soubory pro obsah.

Pro obrázky a další statické prostředky, přidejte je do podsložce s názvem `media`. Pokud vytváříte novou složku pro obsah, přidejte složku médií do nové složky.

Ujistěte se, postupujte podle lze patřičnou syntaxi Markdown. Zobrazit [průvodce správným stylem](./styleguide/template.md) Další informace.

### <a name="example-structure"></a>Ukázková struktura

    docs
        /standard-library
            wstring-convert-class.md
            /media
                wstring-conversion.png

**Krok 5:** odeslat žádost o přijetí změn požádat o (o přijetí změn) z vaší větve do `MicrosoftDocs/cpp-docs/master`.

Pokud vaše žádost o přijetí změn řeší stávající problém, přidejte `Fixes #Issue_Number` – klíčové slovo na zprávu potvrzení nebo popis žádosti o přijetí změn, tak problém může být automaticky uzavřena žádosti o přijetí změn se sloučí. Další informace najdete v tématu [uzavírá chyby prostřednictvím zprávy potvrzení](https://help.github.com/articles/closing-issues-via-commit-messages/).

Tým sady Visual Studio zkontrolujte vaše žádost o přijetí změn, který se vám oznámíme, pokud změna vypadá dobře, nebo pokud jsou nezbytné, aby ho schválit aktualizace/změny.

**Krok 6:** provádět všechny nutné aktualizace vaší větve, jak je popsáno s týmem.

Programu dojde ke sloučení vaší žádosti o přijetí změn do hlavní větve po použití zpětnou vazbu a změny vypadá dobře.

Některé čím dál jsme nasdílení změn všechna potvrzení změn z hlavní větve do živé větve a pak budete moci zobrazit váš příspěvek živě [docs.microsoft.com](https://docs.microsoft.com/cpp/).

## <a name="dos-and-donts"></a>Pro a proti

Níže je krátký seznam potřebnými pravidla, která je třeba mít na paměti, když jsou přispívání do dokumentace k .NET.

- **Není** překvapí nám s žádostí o přijetí změn velké objemy. Místo toho založte problém a vytvořit diskusi tak jsme můžou dohodnout na směru, než investovat velké množství času.
- **PROVEĎTE** čtení [průvodce správným stylem](./styleguide/template.md) a [pro hlasové hovory a tón](./styleguide/voice-tone.md) pokyny.
- **PROVEĎTE** použít [šablony](./styleguide/template.md) soubor jako výchozí bod své práce.
- **PROVEĎTE** vytvořit samostatné větvi ve vašem forku před zahájením práce v článcích.
- **PROVEĎTE** postupujte [pracovního postupu GitHub Flow](https://guides.github.com/introduction/flow/).
- **PROVEĎTE** blogu a tweet (nebo cokoli jiného) vaše příspěvky, často!

> [!NOTE]
> Můžete si všimnout, že některá témata jsou aktuálně po všech pokynů tady zadané a na [průvodce správným stylem](./styleguide/template.md) také. Pracujeme dosahování konzistence v celém webu. Zkontrolujte seznam [hlásit problémy](https://github.com/MicrosoftDocs/cpp-docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) jsme se aktuálně sledování pro tento konkrétní cíl.

## <a name="building-the-docs"></a>Vytváření webu docs

Dokumentace je napsána v [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/) a vytvořené s použitím [DocFX](https://dotnet.github.io/docfx/) a jiné interního nástroje pro publikování/budova. Je hostovaný na [docs.microsoft.com](https://docs.microsoft.com/).

Pokud chcete sestavit dokumentace místně, musíte nainstalovat [DocFX](https://dotnet.github.io/docfx/); nejnovější verze jsou nejlepší.

Existuje několik způsobů, jak používat DocFX a většina z nich se věnuje [DocFX – Příručka Začínáme](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html). Použijte následující pokyny [příkazového řádku na základě](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html#2-use-docfx-as-a-command-line-tool) verzi nástroje. Pokud jste obeznámeni s jinými způsoby uvedené výše na odkaz, můžete použít.

**Poznámka:** aktuálně DocFX vyžaduje rozhraní .NET Framework na Windows nebo Mono (pro systém Linux nebo macOS). Věříme, že budete v budoucnu port až po .NET Core.

Můžete vytvořit a zobrazit jejich náhled výsledný serveru místně s použitím integrovaný webový server. Přejděte `cpp-docs\docs` složky na svůj počítač a zadáte následující příkaz:

> Výchozí -t docfx – slouží

Tím se spustí místním náhledu na [localhost: 8080](http://localhost:8080). Pak můžete zobrazit změny tak, že přejdete do `http://localhost:8080/[path]`, jako například `http://localhost:8080/cpp/visual-cpp-in-visual-studio.html`.

**Poznámka:** místní náhled aktuálně neobsahuje všechny motivy v tuto chvíli tak vzhled a chování nesmí být stejné jako webu s dokumentací. Pracujeme na opravě tohoto prostředí. Také používáme některá vlastní rozšíření pro vložené video, poznámky a zahrnuté dokumenty, které nebudou viditelné ve verzi preview.

## <a name="contributing-to-samples"></a>Přispívání do vzorků

Prozatím zahrnout požadované ukázkový kód jako vložené bloky kódu do článku. Úložiště obsahuje `codesnippets` složka, ale to není připraven pro veřejné příspěvky.

## <a name="contributor-license-agreement"></a>Přispěvatel licenční smlouvy

Musíte podepsat [licenční smlouvy (CLA)](LICENSE) předtím, než se vaše žádost o přijetí změn sloučí. Toto je jednorázový požadavek pro projekty v webu docs.microsoft.com. Další informace o [licenční smlouvy (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) v encyklopedii Wikipedia.

Není nutné k podepsání smlouvy předem. Můžete klonování forku a odeslání vaší žádosti o přijetí změn jako obvykle. Když se vaše žádost o přijetí změn, je klasifikován sloupcem robotem. Pokud je jednoduchá změna (například jste opravili překlep), pak žádosti o přijetí změn je označena CLA není potřeba. V opačném případě je klasifikován jako CLA vyžaduje. Po podepsání CLA aktuální a všechny budoucí žádosti jsou označeny jako CLA podepsané.
