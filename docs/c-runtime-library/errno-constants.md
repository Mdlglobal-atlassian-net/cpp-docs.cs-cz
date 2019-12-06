---
title: errno – konstanty
ms.date: 09/17/2018
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
ms.openlocfilehash: 34f92bedfa9606c90196f2e3a5e47dc341b23aea
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898747"
---
# <a name="errno-constants"></a>errno – konstanty

## <a name="syntax"></a>Syntaxe

```
#include <errno.h>
```

## <a name="remarks"></a>Poznámky

Hodnoty **errno** jsou konstantami přiřazenými [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) v případě různých chybových stavů.

ERRNO. H obsahuje definice hodnot **errno** . Ale ne všechny definice uvedené v ERRNO. H se používá v operačních systémech Windows 32. Některé hodnoty v ERRNO. H je k dispozici pro zachování kompatibility s rodinou operačních systémů UNIX.

Hodnoty **errno** v operačním systému Windows 32 jsou podmnožinou hodnot pro **errno** v systémech Xenix. Proto hodnota **errno** není nutně stejná jako skutečný kód chyby vrácený systémovým voláním z operačních systémů Windows. Pro přístup ke skutečnému kódu chyby operačního systému použijte [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) proměnnou, která obsahuje tuto hodnotu.

Podporovány jsou následující hodnoty **errno** :

|Konstanta|Popis|
|-|-|
|**ECHILD**|Žádné setvářené procesy.|
|**EAGAIN**|Žádné další procesy. Pokus o vytvoření nového procesu se nezdařil, protože neexistují žádné další sloty procesu, nebo není k dispozici dostatek paměti nebo byla dosažena maximální úroveň vnoření.|
|**E2BIG**|Seznam argumentů je příliš dlouhý.|
|**EACCES**|Oprávnění bylo odepřeno. Nastavení oprávnění souboru nepovoluje zadaný přístup. Tato chyba znamená, že došlo k pokusu o přístup k souboru (nebo v některých případech adresáře) způsobem, který je nekompatibilní s atributy souboru.<br/><br/>K této chybě může dojít například při pokusu o čtení ze souboru, který není otevřen, k otevření existujícího souboru jen pro čtení pro zápis nebo pro otevření adresáře místo souboru. V části operační systém MS-DOS verze 3,0 a novější může **EACCES** také znamenat narušení uzamčení nebo sdílení.<br/><br/>K této chybě může dojít také při pokusu o přejmenování souboru nebo adresáře nebo odebrání existujícího adresáře.|
|**EBADF**|Chybné číslo souboru Existují dvě možné příčiny: 1) zadaný popisovač souboru není platná hodnota nebo neodkazuje na otevřený soubor. 2) byl proveden pokus o zápis do souboru nebo zařízení otevřeného pro přístup jen pro čtení.|
|**EDEADLOCK**|Dojde k zablokování prostředků. Argument matematické funkce není v doméně funkce.|
|**EDOM**|Argument Math|
|**EEXIST**|Soubory existují. Byl proveden pokus o vytvoření souboru, který již existuje. Například příznaky **_O_CREAT** a **_O_EXCL** jsou zadány ve volání **_open** , ale pojmenovaný soubor již existuje.|
|**EILSEQ**|Neplatná sekvence bajtů (například v řetězci znakové sady MBCS).|
|**EINVAL**|Neplatný argument. Pro jeden z argumentů funkce byla zadána neplatná hodnota. Například hodnota zadaná pro počátek při umístění ukazatele na soubor (prostřednictvím volání **fseek**) je před začátkem souboru.|
|**EMFILE**|Je otevřeno příliš mnoho souborů. Nejsou k dispozici žádné další popisovače souboru, takže nelze otevřít žádné další soubory.|
|**ENOENT**|Žádný takový soubor nebo adresář neexistuje. Zadaný soubor nebo adresář neexistuje nebo nebyl nalezen. Tato zpráva se může objevit vždy, když zadaný soubor neexistuje nebo pokud součást cesty neurčuje existující adresář.|
|**ENOEXEC**|Chyba formátu Exec. Byl proveden pokus o spuštění souboru, který není spustitelný nebo má neplatný formát spustitelného souboru.|
|**ENOMEM**|Nedostatek jader. K dispozici není dostatek paměti pro pokusy o obsluhu. Tato zpráva se může zobrazit například v případě, že k dispozici není dostatek paměti pro spuštění podřízeného procesu nebo když žádost o přidělení ve **_getcwd** volání nelze splnit.|
|**ENOSPC**|Na zařízení nezbývá žádné místo. V zařízení není k dispozici více místa pro zápis (například když je disk plný).|
|**ERANGE**|Výsledek je příliš velký. Argument matematické funkce je příliš velký, což vedlo k částečné nebo celkové ztrátě významnosti ve výsledku. K této chybě může dojít také v případě, že argument je větší, než se očekávalo (například když je argument buffer **_getcwd** delší, než se očekávalo).|
|**EXDEV**|Propojení mezi zařízeními. Byl proveden pokus o přesunutí souboru na jiné zařízení (pomocí funkce **přejmenování** ).|
|**STRUNCATE**|Výsledkem řetězcové kopie nebo zřetězení je zkrácený řetězec. Viz [_TRUNCATE](../c-runtime-library/truncate.md).

Pro kompatibilitu s POSIX jsou podporovány následující hodnoty. Jsou to povinné hodnoty v systémech jiných než POSIX.

```C
#define E2BIG /* argument list too long */
#define EACCES /* permission denied */
#define EADDRINUSE /* address in use */
#define EADDRNOTAVAIL /* address not available */
#define EAFNOSUPPORT /* address family not supported */
#define EAGAIN /* resource unavailable try again */
#define EALREADY /* connection already in progress */
#define EBADF /* bad file descriptor */
#define EBADMSG /* bad message */
#define EBUSY /* device or resource busy */
#define ECANCELED /* operation canceled */
#define ECHILD /* no child process */
#define ECONNABORTED /* connection aborted */
#define ECONNREFUSED /* connection refused */
#define ECONNRESET /* connection reset */
#define EDEADLK /* resource deadlock would occur */
#define EDESTADDRREQ /* destination address required */
#define EDOM /* argument out of domain */
#define EEXIST /* file exists */
#define EFAULT /* bad address */
#define EFBIG /* file too large */
#define EHOSTUNREACH /* host unreachable */
#define EIDRM /* identifier removed */
#define EILSEQ /* illegal byte sequence */
#define EINPROGRESS /* operation in progress */
#define EINTR /* interrupted */
#define EINVAL /* invalid argument */
#define EIO /* io error */
#define EISCONN /* already connected */
#define EISDIR /* is a directory */
#define ELOOP /* too many synbolic link levels */
#define EMFILE /* too many files open */
#define EMLINK /* too many links */
#define EMSGSIZE /* message size */
#define ENAMETOOLONG /* filename too long */
#define ENETDOWN /* network down */
#define ENETRESET /* network reset */
#define ENETUNREACH /* network unreachable */
#define ENFILE /* too many files open in system */
#define ENOBUFS /* no buffer space */
#define ENODATA /* no message available */
#define ENODEV /* no such device */
#define ENOENT /* no such file or directory */
#define ENOEXEC /* executable format error */
#define ENOLCK /* no lock available */
#define ENOLINK /* no link */
#define ENOMEM /* not enough memory */
#define ENOMSG /* no message */
#define ENOPROTOOPT /* no protocol option */
#define ENOSPC /* no space on device */
#define ENOSR /* no stream resources */
#define ENOSTR /* not a stream */
#define ENOSYS /* function not supported */
#define ENOTCONN /* not connected */
#define ENOTDIR /* not a directory */
#define ENOTEMPTY /* directory not empty */
#define ENOTRECOVERABLE /* state not recoverable */
#define ENOTSOCK /* not a socket */
#define ENOTSUP /* not supported */
#define ENOTTY /* inappropriate io control operation */
#define ENXIO /* no such device or address */
#define EOPNOTSUPP /* operation not supported */
#define EOTHER /* other */
#define EOVERFLOW /* value too large */
#define EOWNERDEAD /* owner dead */
#define EPERM /* operation not permitted */
#define EPIPE /* broken pipe */
#define EPROTO /* protocol error */
#define EPROTONOSUPPORT /* protocol not supported */
#define EPROTOTYPE /* wrong protocol type */
#define ERANGE /* result out of range */
#define EROFS /* read only file system */
#define ESPIPE /* invalid seek */
#define ESRCH /* no such process */
#define ETIME /* stream timeout */
#define ETIMEDOUT /* timed out */
#define ETXTBSY /* text file busy */
#define EWOULDBLOCK /* operation would block */
#define EXDEV /* cross device link */
```

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)
