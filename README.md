## Rogue-like ����!
 
������������ � ������� �����, ��������:

  `.................K`
  
  `....Z.............`
  
  `..Z.........######`
  
  `.................#`
  
  `......D........P.#`

� ���������� ����� ��������� ������� (WASD ��� ���������)

���� ���� ���������, ����� ����������� ������ ����� ��� ��������� ����

��������� �� ������ �������� �� ������� ����� (� ���� �� ������ ������ ��� ����!).

������������ ���������� ���� � ������ ���� �� �����������.


��� ���������� � ������ -fsanitize=address ��� ��� �� ������ ������. ��������� ��� �������.


������/����������� �� ����������:

### ������� ����� � ����� ��������
class Character:

private:

hp - ���������� �����

damage - ���������� ���������� ����� 

sym - char, ������� ������ �������� ������������ �� �����


x, y - ���������� (����� ������� ������� ��������� Point ��� �� ��������)

�������� max_hp - ������������ ���������� ����� ��� ���������� ������� ����

�������� ����

public:

GetPos - �������, ����������� ����������

GetHp, GetDamage, GetSym - ������� ��� hp, damage � sym �������������� 



����� Character ������ ���� �����������


�� Character ������ �������������:

Knight - ��������, ������� �� ����������. (K)

Princess - ���������, �� ��� ����� ���������, ����� ��������. ��� ������ ����� �� �����, ����� ���� �� ������� (P)

Zombie - ������, ������� �������� (��� �� ����������� � �����) ������������ �� ����� (Z)

Dragon - ���� ����, ������� ��� ����� (D)

Wall - ����� - �����, ������ �� ������. ����� ��� ������ ������ (#)

����������� ����� ������������ ����� � ������� �� ������ Monster(Enemy), ������� �� � ���� ������� ������������ �� Character-�

����� ������� �������������� ������� ����� Actor/GameObject, �� �������� ����� ������������� �������� Wall � Character � ��� ��������� �������. �� Character -- ������ ��, ��� �������� �����-�� ������� ���������� �� �����.


### �����
� ��� ������ ���� ����� (class Map), � ������� ������ ��������� ���� �����

����� ������ ������������ �� �����. ����������� ������ �������������� Factory ��� �������� ������� ������ ��������� �� ������� � ����� � ������. 

### Game loop

����� ������ ���� �����, ����������� ����� ������� ���������. �������� �������� ���� ����.

� ��� ����� ���� ������ ������� ������ ���������� �� �����.

### ����� ��������
� ����� ���������� ����������� �������� �� ���� ����������, �� �� ��������� ����, ����� �������������� ���, ��������� �� ����� ���������� ����� �������� �����. �� ������ ���� ����������, �� ������������� ������� �� ������� �������. RAII ������ ����������� (����� ������������ � ������� unique_ptr, shared_ptr).


P.S. �������� ���������� �� ����������� ������ ��������������� ����, ��� ������� �����. 

�������� �������� ����������, ������ ��������� ��������, ��� ��� ���������.


## 2� ����� Rogue-like ����.

1. ����������� ������� character_ptr Collide(character_ptr). Collide ��������� ��� ������������ 2� ���������� � ��������� �� ��������������.
���������� ��� ���� ��� ����� ����������. ����������� double dispatch.
����� �������������� ����������� � ���������� �����������, �� �� ������ ���� ���� �� ��� ��������� � ������������ ����.

2. ���� �� ���� ��� �������� ������ ��������� ��������. ��������������, ������ ��������� ����� Projectile (��������� �� Character). ��� ����������� projectile-�� � ������� ����� ������������ ������� (^v). ��� ������������ projectile-� � ����� ������, projectile ������� ����� ��������� ������������� ���� � ��������. ��� ������������ � ������� ������, projectile ����� �������� ��� �� �������� ���� �� ������ ����������. ��� ������������ �� ������ ��� �������� �����, projectile ��� �� ������ ��������.

3. ��� �������� ���� ������ ����� ��������.

4. ������ ��������� ������� (����� AidKit, ��������� �� ������-������ ������ � Character ������). ��� ������������ ������ � ��������, �� ������ �������� �� �����-�� ������������� ����� (�� ��� ���� ��� hp �� ����� ��������� max_hp), ����� ���� ������� ������ ��������. ������ ��������� ����� ������������ �������, ��� ����� "������� ��" (�� ���� ����������). Projectile-� ����� ��������� ��� �� ��������� �������. Projectile ��� � ������ ������� ����� ������������� �� Actor/GameObject (����� ������ ���� ��� ������� ������� � ����������).



## 3� ����� Rogue-like ����.

1. ���������� ���������� ncurses (pdcurses �� �����), ����������� �� ��� ��������� ����� � �������. ����� ������������ �����-������ ������ ����������, ���� �������.

2. ��� ��������� ������ ��������� � config-�����. ����� �������, ��� ���������, ��������, hp �����, �� ����� ����� ����������������� ����. �� ����������� ������ ����������, ����� ������������ ������������ ���������� ��� json/yaml/xml/ini � �.�.

3. ���� ���� ������ ���� realtime - ������� ������ ������ �� ����� ����, ��� �� �������� ���, � ��� � �����-�� ���������� ������� (��������, ��� � �������). ��� ����������� ���������� ������� ����� ����������� ncurses.



����� � �������� 3 �������, ��� ����������� ������. �� 1 � 2 �� ������ �������� �� 6 ������, �� 1, 2 � 3 �� 8��. ��� ��� ���������� � ���� �� ������ ��������� � �������� ��������� � ��������. �� ������ ��������� �������� ��� �������� -1 ����. �� 10 ������ ����� ��������, ������������� ������ �����-������ ���������� �����, ��������:

1. ����������� ����� (1 ����)
2. �������� ���� (1 ����)
3. ������� ��������� (1-2 ����� � ����������� �� ���������)
4. ����� ����� (1 ����)
5. ������ �������� ����-������� � ��������������� ������� (�������������� �������� ������� ���������) (1-2 ����� � ����������� �� ���������)

��� ��� ������ ������, ��� ���������:)
