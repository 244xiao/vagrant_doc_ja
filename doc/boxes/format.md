# BOX �t�@�C���t�H�[�}�b�g

�ߋ��A Box �� VirtualBox ���G�N�X�|�[�g���� [tar �t�@�C��](http://en.wikipedia.org/wiki/Tar_(computing))�����ł����BVagrant �͕����� Provider ���T�|�[�g�������߁A���� Box �t�@�C���͊e Provider ���ɈقȂ� tar �t�@�C���ɂȂ��Ă��܂��B�܂� Box �� tar �t�@�C���ł����A���݁A�I�v�V������ [gzip](http://en.wikipedia.org/wiki/Gzip) ���k������܂��B

Vagrant 1.0.x �� VirtualBox �̂��߂ɍ��ꂽ Box �t�@�C���� Vagrant 1.1 + �� VirtualBox Provider �ł����삵�����܂��B

Box ���ɕK�v�ȗB��̃t�@�C���� "metadata.json" �t�@�C���ł��B���� [JSON](http://www.json.org/) �t�@�C���� Box �Ɋւ��郁�^�f�[�^���܂ނ��Ƃ̂ł���g�b�v���x���̃I�u�W�F�N�g�������Ă��܂��BVagrant �ł̓��^�f�[�^�� "provider" �L�[�� ����Box �� Provider �̖��O���K�v�ł��B

VirtualBox �� Box �� "metadata.json" �t�@�C���F

```
{
  "provider": "virtualbox"
}
```

Box ��ǉ�����Ƃ��A metadata.json �t�@�C�������݂��Ȃ��A�܂��͏��Ȃ��Ƃ� "provider" �L�[�����L���� JSON ���܂܂�Ă��Ȃ��t�@�C���̏ꍇ�́A Vagrant �̓G���[�ɂȂ�܂��B

