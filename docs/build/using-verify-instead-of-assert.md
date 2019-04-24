---
title: Použití příkazu VERIFY místo ASSERT
ms.date: 11/04/2016
f1_keywords:
- assert
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: e6903616f8b4250b3d67db333be4fc17e8328952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326219"
---
# <a name="using-verify-instead-of-assert"></a>Použití příkazu VERIFY místo ASSERT

Předpokládejme, že když spustíte ladicí verze aplikace knihovny MFC, nejsou žádné problémy. Ale verzi stejné aplikace dojde k chybě, vrátí nesprávné výsledky, a/nebo vykazuje nějaké neobvyklé chování.

Tento problém může být způsobena umístíte důležité kód kontrolní příkaz k ověření, že funguje správně. Protože příkazů ASSERT, jsou zakomentované v sestavení pro vydání aplikace knihovny MFC, nespustí se kód v sestavení pro vydání.

Pokud používáte ASSERT potvrďte, že volání funkce úspěšné, zvažte použití [OVĚŘTE](../mfc/reference/diagnostic-services.md#verify) místo. VERIFY – makro vyhodnocuje svoje vlastní argumenty v obou ladění a verze sestavení aplikace.

Jiné upřednostňované technikou je návratová hodnota funkce přiřadit dočasné proměnné a otestujte proměnné v příkazu ASSERT.

Zkontrolujte následující fragment kódu:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Tento kód se spustí dokonale v ladicí verzi aplikace knihovny MFC. Pokud volání `calloc( )` selže, diagnostickou zprávu, která zahrnuje soubor a číslo řádku se zobrazí. Nicméně v sestavení prodejní verze aplikace knihovny MFC:

- volání `calloc( )` se nikdy neprovádí, byste museli opustit `buf` neinicializované nebo

- `strcpy_s( )` kopie "`Hello, World`" do náhodných část paměti, může být selhání aplikace nebo může způsobit systém přestane reagovat, nebo

- `free()` pokusy o uvolnění paměti, který se nikdy.

Použití metody ASSERT správně, by měla být změněna vzorový kód takto:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Nebo můžete místo toho použít ověřte, zda:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Viz také:

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
