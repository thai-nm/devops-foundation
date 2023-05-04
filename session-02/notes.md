- Pod definition
- Slides:
  - slide 3: 
    - Network Address Translation (NAT) is a process in which one or more local IP address is translated into one or more Global IP address and vice versa in order to provide Internet access to the local hosts. 
  - slide 4:
  - - Có 4 network level trong cụm k8s: 
      - container: network giữa các container trong cùng pod
      - pod: network giữa các pod trong cùng node
      - node: network giữa các node trong cùng cluster
      - cluster: network từ cluster ra ngoài
    - Kubernetes IP addresses exist at the Pod scope - containers within a Pod share their network namespaces - including their IP address and MAC address. This means that containers within a Pod can all reach each other's ports on localhost. This also means that containers within a Pod must coordinate port usage, but this is no different from processes in a VM.
  - slide 5:
    -  Node sẽ có:
       -  network interface eth0: đóng vai trò là nơi tiếp nhận packet từ internet.
       -  bridge: đóng vai trò như một switch, đưa packet tới network interface đích
       -  eth0-veth0: cặp network interface đóng vai trò nối network của pod tới network host.
  - slide 6:
    -  Mỗi Pod có một địa chỉ IP độc nhất trên toàn cluster, các container trong pod chia sẻ chung một network, do đó sẽ sử dụng chung network interface, bao gồm địa chỉ IP và MAC. Điều này cũng có nghĩa port number của từng container cũng sẽ phải khác nhau.
 
  - slide 7:
    - Nếu các bạn sử dụng kubeadm để khởi tạo cluster thì sẽ thấy pod CIDR range được sử dụng khi tạo cluster.
    - Pod CIDR range có thể được tìm thấy từ command:
      ```bash
      kubectl cluster-info dump | grep cluster-cidr
      ```
    - Từ pod này sang pod khác có thể communicate với nhau thông qua IP của pod 
    **DEMO**: tạo 2 pod nginx, exec vào 1 pod và call tới pod còn lại

  - slide 8:
    - Đường đi của packet từ pod ở node này tới một pod ở node khác sẽ là:
      - từ pod tới bridge của node thông qua cặp network interface eth0-veth1
      - tại bridge của node, không tìm thấy interface cần route tới, packet sẽ được đưa tới default route eht0 và route tới node cần tới.
      - Tới node cần tới, đi qua bridge của node đó và qua cặp veth-eth của pod cần tới và tới pod đó.

  - slide 9:
    - Một vài vấn đề với IP của pod
    - Kubernetes sử  dụng Service để giải quyết

  - slide 10:
    - mô tả một service và cách service hoạt động 
    **DEMO**: 