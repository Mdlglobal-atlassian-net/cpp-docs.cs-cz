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
ms.openlocfilehash: c7c623b81d626b3d653dbd731521ffe2649671ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645598"
---
# <a name="errno-constants"></a>errno – konstanty

## <a name="syntax"></a>Syntaxe

```

#include <errno.h>
```

## <a name="remarks"></a>Poznámky

**Errno** hodnoty jsou konstanty, které jsou přiřazeny [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) v případě různé chybové stavy.

KÓD CHYBY. H obsahuje definice **errno** hodnoty. Ale ne všechny definice podle ERRNO. H se používají v operačních systémech Windows 32-bit. Některé hodnoty v ERRNO. H jsou k dispozici pro zachování kompatibility se systémem UNIX řady operačních systémů.

**Errno** podmnožinu hodnoty jsou hodnoty v operačním systému Windows 32-bit **errno** XENIX systémy. To znamená **errno** hodnota není nutně stejný jako skutečný chybový kód vrácený voláním systému od operačních systémů Windows. Chcete-li získat přístup k kód chyby skutečné operačního systému, použijte [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) proměnnou, která obsahuje tuto hodnotu.

Následující **errno** hodnoty jsou podporovány:

|Konstanta|Popis|
|-|-|
|**ECHILD**|Žádné vytvářené procesy.|
|**EAGAIN**|Žádné další procesy. Pokus o vytvoření nového procesu se nezdařila, protože neexistují žádné další proces sloty, nebo není dostatek paměti nebo bylo dosaženo maximální úrovně vnoření.|
|**E2BIG**|Seznam argumentů je příliš dlouhý.|
|**EACCES**|Oprávnění byla odepřena. Nastavení oprávnění k souboru neumožňuje zadaný přístup. Tato chyba označuje, že byl proveden pokus o přístup k souboru (nebo v některých případech se do adresáře) v způsobem, který je kompatibilní s atributy souboru.<br/><br/>Této chybě může dojít například při pokusu o čtení ze souboru, který není otevřený, otevřete existující soubor jen pro čtení pro zápis, nebo otevřete adresář, nikoli soubor. V části zástupného kódu MS-DOS verze operačních systémů, 3.0 a vyšší **EACCES** může také znamenat uzamčení nebo narušení sdílení.<br/><br/>Této chybě může dojít také při pokusu o přejmenování souboru nebo adresáře nebo odstranění existující adresář.|
|**EBADF**|Chybné číslo souboru. Existují dva možné příčiny: 1) popisovače zadaný soubor není platnou hodnotou nebo neodkazuje na otevřený soubor. 2) byl k pokusu o zápis do souboru nebo zařízení pro přístup jen pro čtení.|
|**EDEADLOCK**|By k vzájemnému zablokování prostředků. Argument matematické funkce není v doméně funkce.|
|**EDOM**|Matematický argument.|
|**EEXIST**|Soubory existují. Byl proveden pokus o vytvoření souboru, který již existuje. Například **_O_CREAT** a **_O_EXCL** příznaky jsou určené v **_Otevřít** volání, ale soubor s názvem již existuje.|
|**EILSEQ**|Neplatné pořadí bajtů (například v řetězci znakové sady MBCS).|
|**EINVAL**|Neplatný argument. Neplatná hodnota byl zadán pro jeden z argumentů funkce. Například hodnota pro původ zadané při umístění ukazatele souboru (prostřednictvím volání **fseek**) je před začátkem soubor.|
|**EMFILE**|Příliš mnoho otevřených souborů. Žádné další popisovače souborů, které jsou k dispozici, takže žádné další soubory můžete otevřít.|
|**ENOENT**|Žádný odpovídající soubor nebo adresář. Zadaný soubor nebo adresář neexistuje nebo nebyl nalezen. Tato zpráva může dojít při každém zadaný soubor neexistuje nebo součást cesty nespecifikuje existující adresář.|
|**ENOEXEC**|Chyba formátu exec. Došlo pokusu o spuštění souboru, který není spustitelný soubor nebo, který má neplatný formát spustitelného souboru.|
|**ENOMEM**|Není k dispozici dostatek jader. Nedostatek paměti je k dispozici pro pokus o operátor. Například tato zpráva může dojít, když není dostatek paměti ke spuštění podřízeného procesu, nebo když požádat o přidělení paměti v **_getcwd** volání nedokáže splnit.|
|**ENOSPC**|Není dostatek místa. na zařízení. Žádné další místo pro zápis je k dispozici na zařízení (třeba při zaplnění disku).|
|**ERANGE**|Výsledek je příliš velký. Argument matematické funkce je moc velká, čímž částečné nebo úplné dojde ke ztrátě významu výsledku. Této chybě může dojít také v dalších funkcí, pokud argument je větší, než bylo očekáváno (například když *vyrovnávací paměti* argument **_getcwd** je delší, než se očekávalo).|
|**EXDEV**|Odkaz mezi zařízeními. Byl proveden pokus o přesunutí souboru do různých zařízení (pomocí **přejmenovat** funkce).|
|**STRUNCATE**|Výsledkem zkrácený řetězec je řetězec kopírování nebo zřetězení. Zobrazit [_TRUNCATE](../c-runtime-library/truncate.md).

Následující hodnoty jsou podporovány pro kompatibilitu s Posix. Jsou požadované hodnoty v systémech bez Posix.

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

## <a name="see-also"></a>Viz také

[Globální konstanty](../c-runtime-library/global-constants.md)