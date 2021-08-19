## JSX.ELement

`JSX.Element` �� 1���� ����Ʈ Element�� ����Ѵ�. (string�� X)
���� `JSX.ELement`�� ���� ����Ʈ Element�� �ް� �ʹٸ�

```tsx
children: JSX.Element | JSX.Element[];
```

�̷��� ����� �Ѵ�.

## ReactChild

`JSX.Element`�� ����ȣȯ���ν�, string�� ������� �ʴ´�.
���� ���� ����Ʈ Element�� �ް� string���� �ް� ������ �̷��� ����������Ѵ�.

```tsx
children: JSX.Element | JSX.Element[] | string | string[];
```

������ �̷��� �������� `ReactChild`�� ����ȴ�.

```tsx
children: ReactChild | ReactChild[];
```

������ �̰͵� ���� ����Ʈ Element�� ������� �ʾƼ� ���� ������ �ʿ��ϴ�.

## ReactNode

������

```tsx
children: ReactChild | ReactChild[];
```

�̷��� �� �ʿ����

```tsx
children: ReactNode;
```

�̷��� �� �� �ִ�.
�̰� ���� Element�� �ǰ�, string�� �ǰ�, numbers�� �ǰ�, fragments�� �ǰ�, portals�� �ǰ�.. �ٵȴ�!
