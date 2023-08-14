## Pod oluşturma:

```bash
kubectl run nginx-pod --image=nginx
```
Bu komut, "nginx-pod" adında bir pod oluşturur ve nginx imajını kullanır.

## Replika set oluşturma:

```bash
kubectl run nginx-replicaset --image=nginx --replicas=3
```
Bu komut, "nginx-replicaset" adında bir replika set oluşturur ve içinde 3 adet nginx podunu çalıştırır.

## kubectl create deployment:

```bash
kubectl create deployment nginx-deployment --image=nginx
```
Bu komut, "nginx-deployment" adında bir deployment oluşturur ve nginx imajını kullanarak bu deployment'a bir pod oluşturur.

## kubectl get deployments:

```bash
kubectl get deployments
```
Bu komut, mevcut deployment'ları listeler. Oluşturduğunuz "nginx-deployment" gibi bir deployment'ı görüntülemenizi sağlar.

```bash
kubectl get deployment --namespace dev
```
Bu komutu kullanarak, dev ad alanında çalışan tüm deployment'ları listeleyebilir ve bunların durumlarını, replika sayılarını ve diğer ilgili bilgileri görebilirsiniz. Bu bilgiler, uygulamalarınızın durumunu kontrol etmek ve gerektiğinde yönetim işlemlerini gerçekleştirmek için faydalı olabilir.

## kubectl get pods:

```bash
kubectl get pods
```
Bu komut, mevcut podları listeler. "nginx-deployment" deployment'ı altında çalışan podları görüntülemek için kullanabilirsiniz.

```bash
kubectl get pods -o wide
```
Bu komut ile Kubernetes kümesindeki podların geniş bir görünümünü listeler. -o wide bayrağı, podların ayrıntılı bilgilerini içeren ek sütunları görüntülemek için kullanılır. Bu geniş görünüm, podların düğümler üzerinde nasıl dağıldığını, IP adreslerini ve diğer ilgili ayrıntıları görmek için faydalı olabilir.

## kubectl expose deployment:

```bash
kubectl expose deployment nginx-deployment --port=80 --type=NodePort
```
Bu komut, "nginx-deployment" deployment'ını dış dünyadan erişilebilir hale getirir. 80 portunda bir servis oluşturur ve tipini NodePort olarak belirler.

## kubectl get services:
```bash
kubectl get services
```

```bash
kubectl get svc
```
Bu komut, mevcut servisleri listeler. "nginx-deployment" deployment'ınızın oluşturduğu servisi görüntülemek için kullanabilirsiniz.

## kubectl scale deployment:

```bash
kubectl scale deployment nginx-deployment --replicas=3
```
Bu komut, "nginx-deployment" deployment'ının replika sayısını 3'e ayarlar. Bu şekilde, nginx imajını kullanarak çalışan podların sayısını artırabilir veya azaltabilirsiniz.

## kubectl delete deployment:

```bash
kubectl delete deployment nginx-deployment
```
Bu komut, "nginx-deployment" deployment'ını siler. Böylece deployment'a bağlı olan podlar ve servis de otomatik olarak kaldırılır.

## kubectl describe deployment:

```bash
kubectl describe deployment nginx-deployment
```
Bu komut, "nginx-deployment" deployment'ı hakkında ayrıntılı bilgi sağlar. Deployment'ın durumu, replica sayısı, oluşturulan podlar ve diğer önemli bilgileri görüntüler.

## kubectl edit deployment:

```bash
kubectl edit deployment nginx-deployment
```
Bu komut, "nginx-deployment" deployment'ının YAML tanımını düzenler. Bir metin düzenleyici açarak deployment'ın YAML dosyasını düzenlemenize olanak tanır. Bu şekilde, deployment'ın özelliklerini veya konfigürasyonunu değiştirebilirsiniz.

## kubectl rollout status:

```bash
kubectl rollout status deployment/nginx-deployment
```
Bu komut, "nginx-deployment" deployment'ının güncelleme durumunu takip eder. Güncelleme işleminin tamamlanıp tamamlanmadığını veya hala devam edip etmediğini kontrol etmenize olanak sağlar.

## kubectl rollout history:

```bash
kubectl rollout history deployment/nginx-deployment
```
Bu komut, "nginx-deployment" deployment'ının güncelleme geçmişini görüntüler. Hangi sürümlerin dağıtıldığını, geri alındığını veya yeniden başlatıldığını görmek için kullanılabilir.

## kubectl rollout undo:

```bash
kubectl rollout undo deployment/nginx-deployment
```
Bu komut, "nginx-deployment" deployment'ını bir önceki sürüme geri alır. Eğer bir güncelleme yapıldıysa ve hatalar meydana geldiyse, bu komutla önceki sürüme dönebilirsiniz.

## kubectl exec:

```bash
kubectl exec -it <pod-adı> -- /bin/bash
```
```bash
kubectl exec -ti nginx sh
```

```bash
curl http://10.130.139.109:80 
```
Bu komut, belirli bir pod içinde bir komut çalıştırmanızı sağlar. Örneğin, yukarıdaki komut, <pod-adı> olarak belirtilen pod içinde etkileşimli bir bash kabuğu açar. Ardından nginx'e cluster ip üzerinden erişmek için örnek bir komut gösterilmiştir.(curl)

## kubectl apply:

```bash
kubectl apply -f deployment.yaml
```
Bu komut, bir YAML dosyasındaki tanımlamaları uygular ve kaynakları oluşturur veya günceller. deployment.yaml kısmını ilgili YAML dosyasının adıyla değiştirerek kullanabilirsiniz.

## kubectl delete:

```bash
kubectl delete deployment nginx-deployment
```
Bu komut, belirli bir deployment'ı siler. "nginx-deployment" deployment'ını silmek için kullanabilirsiniz.

## kubectl dry-run:

```bash
kubectl run nginx2 --image nginx --dry-run=client -o yaml
```
Bu komut bir Deployment veya Pod YAML dosyasını oluşturmadan önce dry-run modunda çalıştırarak YAML çıktısını almanızı sağlar. Bu şekilde, YAML dosyasının doğru bir şekilde oluşturulduğunu doğrulayabilir ve gerektiğinde düzenlemeler yapabilirsiniz.

## kubectl explain:

```bash
kubectl explain pod.apiVersion
```

```bash
kubectl explain service.apiVersion
```

Bu komut, belirtilen apiVersion değeri için Kubernetes API dokümantasyonunu görüntüler. Bu komutu kullanarak, bir API versiyonu veya belirli bir kaynak türü için desteklenen alanları, özellikleri ve açıklamalarını öğrenebilirsiniz.

## kubectl create:

```bash
kubectl create -f replicaSet.yaml 
```
Bu komut, belirtilen YAML dosyasındaki ReplicaSet tanımını kullanarak bir ReplicaSet oluşturur.

Ayrıca;

```bash
kubectl create namespace dev
```
```bash
kubectl create namespace test
```
Bu komutlar ile dev, test ve production ortamları tek bir cluster üzerinde birbirinden izole ortamlar oluşturulur.

## minikube service:

```bash
minikube service tomcat-deployment --url
```
minikube service komutu, yerel bir Kubernetes kümesindeki bir servisi dış dünyaya açmak ve servisin URL'sini almak için kullanılır. İstediğiniz komutu kullanarak tomcat-deployment adlı bir servisin URL'sini alabilirsiniz. Bu komut çalıştırıldığında, tomcat-deployment adlı servis için bir URL döndürülür. Bu URL, servise erişmek için kullanabileceğiniz dışarıdan erişilebilir bir adresi temsil eder.

## kubectl set image:

```bash
kubectl set image deployment/tomcat-deployment tomcat=tomcat:8.0
```

```bash
kubectl set image komutu, Kubernetes ortamında bir dağıtımın içindeki bir konteynerin görüntüsünü güncellemek için kullanılır.
```
İşte komutun parçalarının anlamları:

set image: Bu, komutun "görüntüyü ayarla" eylemini gerçekleştireceğini belirtir.
deployment/tomcat-deployment: Bu, güncellemeyi yapmak istediğiniz dağıtımın adını belirtir. deployment/ ön eki, bu kaynağın bir dağıtım olduğunu belirtir.
tomcat: Bu, güncellemek istediğiniz konteynerin adını belirtir.
tomcat:8.0: Bu, konteynerin güncellenmiş görüntüsünü belirtir. tomcat adlı konteynerin 8.0 sürümünü kullanmak istediğinizi gösterir.
Bu komut, belirtilen dağıtımda bulunan bir konteynerin görüntüsünü günceller. Yeni bir görüntü belirtilerek, uygulama veya hizmetin yeni bir sürümünü dağıtabilir veya mevcut bir sürümü güncelleyebilirsiniz. Görüntü güncellemesi yapıldığında, Kubernetes dağıtımı otomatik olarak yeni görüntüyü kullanarak konteynerleri yeniden başlatır ve uygulamanın güncellenmiş sürümünü çalıştırır.
