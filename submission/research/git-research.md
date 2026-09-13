1\. git squash



الـsquash بيجمع كذا commit صغيرة في commit واحدة واضحة، بدل ما الـhistory يبقى مليان commits زي fix bug وfix validation.

هو مش command لوحده، وغالبًا بنعمله باستخدام interactive rebase.



git rebase -i main



Scenario:

لو شغال على Order feature في مشروع ASP.NET Core وعملت commits زي Add order endpoint وFix validation وFix order bug، بعمل لهم squash قبل الـmerge عشان يظهروا في الـhistory كـcommit واحدة واضحة زي Add order management feature.



الأفضل أعمل squash على branch بتاعي أنا، لأنه بيعمل rewrite للـhistory.





2\. git merge vs git rebase



git merge بيجمع تغييرات الـ2 branches مع بعض وبيحافظ على الـhistory زي ما حصل، وغالبًا بيضيف merge commit.



git rebase بياخد commits بتاعت الـfeature branch ويحطها فوق آخر commit في main، فبيخلي الـhistory linear وأنضف.



Scenario:

لو عايز أحافظ على شكل الـhistory الحقيقي بتاع الشغل بين الـbranches بستخدم merge.

ولو الـfeature branch بتاعي وعايز أرتب الـhistory قبل ما أعمل merge على main، ممكن أستخدم rebase.





3\. git help



git help بيفتح الـdocumentation لأي Git command وبيوريك الـoptions والـflags المتاحة.



git help <command>



git help rebase



Scenario:

لو نسيت option في git rebase أو عايز أعرف command بتتستخدم إزاي، بستخدم git help بدل ما أعتمد على الحفظ.





4\. git cherry-pick



git cherry-pick بياخد commit معينة من branch تاني وبيطبقها على الـbranch الحالي، من غير ما أعمل merge لكل الـbranch.



git cherry-pick <commit-hash>



Scenario:

لو عندي bug fix موجودة على branch معين ومحتاجها بسرعة على main من غير باقي التغييرات، بستخدم cherry-pick.





5\. git clean



git clean بيشيل الـuntracked files والـfolders من الـworking directory.



git clean -fd



Scenario:

لو اتكونت files أو folders بعد الـbuild ومش tracked by Git، بستخدم git clean عشان أنضف الـworking directory.



لازم أكون متأكد من الملفات اللي هيتمسحوا قبل ما أنفذه.





6\. git grep



git grep بيعمل search عن word أو text جوه الملفات اللي tracked by Git في الـrepository.



git grep "PaymentService"



Scenario:

لو عايز أعرف كل الأماكن اللي فيها PaymentService أو اسم method معينة، بستخدم git grep بدل ما أفتح الملفات واحدة واحدة.





7\. git blame



git blame بيوريك آخر commit وآخر developer عدّل كل line في file معينة.



git blame PaymentService.cs



Scenario:

لو لقيت line فيها bug وعايز أعرف التغيير ده جه من أنهي commit أو مين آخر حد عدّله، بستخدم git blame.





8\. git bisect



git bisect بيساعدني أحدد الـcommit اللي دخلت الـbug باستخدام Binary Search بين commit سليمة وcommit فيها المشكلة.



git bisect start

git bisect bad

git bisect good <commit-hash>



Scenario:

لو المشروع كان شغال كويس من كام commit وبعدها ظهرت bug، بستخدم git bisect عشان أوصل للـcommit اللي سببتها أسرع من إني أجرب كل commit واحدة واحدة.





9\. git shortlog



git shortlog بيطلع summary للـcommits وبيجمعها حسب كل contributor.



git shortlog -s -n



الـ-s بيعرض عدد الـcommits لكل contributor، والـ-n بيرتبهم حسب العدد.



Scenario:

لو عايز أشوف عدد الـcommits لكل developer في الـrepository، بستخدم git shortlog.





10\. git prune



git prune بيشيل الـGit objects اللي بقت unreachable ومفيش branch أو tag بيشير لها.



git prune



Scenario:

لو فيه commits أو objects قديمة بقت unreachable بعد حذف branches أو rewrite للـhistory، git prune ممكن يشيلها نهائيًا من الـrepository.





11\. git worktree



git worktree بيخليني أشتغل على أكتر من branch في folders مختلفة من نفس الـrepository، من غير ما أعمل clone جديد.



git worktree add ../fix fix-branch



Scenario:

لو شغال على feature branch وفجأة محتاج أعمل bug fix سريع على branch تاني، بستخدم git worktree بدل ما أوقف شغلي الحالي أو أعمل clone جديد.





12\. git verify-commit



git verify-commit بيعمل verify إن الـcommit عليها signature صحيحة زي GPG أو SSH وإن الـsignature دي valid.



git verify-commit <commit-hash>



Scenario:

لو الـteam بيطلب signed commits، بستخدم git verify-commit عشان أتأكد إن الـcommit متوقعة صح قبل ما أعتمدها.





13\. git filter-repo



git filter-repo بيعمل rewrite للـGit history، وده مفيد لو محتاج أشيل file أو secret من كل الـcommits القديمة.



Scenario:

لو رفعت API key بالغلط في commit قديمة، حذفها من آخر commit مش كفاية لأنها لسه موجودة في الـhistory.

وقتها بستخدم git filter-repo عشان أشيلها من كل الـhistory.

