# file upload to s3

- 概要
  - CakePHP3にて、S3にファイルをアップロードする方法

- 事前準備
  - aws-sdk-phpをcomposerでインストールしておく
  ```bash
  $ composer require aws/aws-sdk-php
  ```

- ソースコード
  - config/.env
  ```.env
  export ITEM_IMAGE_PATH = 'upload/images/'
  export S3_BUCKET_NAME = '*******'
  export S3_ACCESS_KEY = '*******'
  export S3_SECRET_KEY = '*******'
  export S3_REGION = '*******'
  export S3_VERSION = '*******'
  ```

  - Model/S3Manager.php
  ``` S3Manager.php
  <?php
  namespace App\Model\Utility;

  use Cake\Log\Log;
  use Aws\S3\Exception\S3Exception;
  use Aws\S3\S3Client;

  class S3Manager
  {
      private $_s3Client;

      /**
      * __construct method
      *
      * @return void
      */
      function __construct()
      {
          $this->_s3Client = new S3Client([
              'credentials' => [
                  'key' => env('S3_ACCESS_KEY'),
                  'secret' => env('S3_SECRET_KEY'),
              ],
              'region' => env('S3_REGION'),
              'version' => env('S3_VERSION'),
          ]);
      }

      /**
      * putObject method
      *
      * @param string $directory
      * @param string $baseFileName
      * @param string $newFileName
      * @return boolean
      */
      public function putObject($directory, $baseFileName, $newFileName)
      {
          $ret = false;
          try {
              $fullPath = $directory . $baseFileName;
              $result = $this->_s3Client->putObject([
                  'Bucket' => env('S3_BUCKET_NAME'),
                  'Key' => env('ITEM_IMAGE_PATH') . $newFileName,
                  'SourceFile' => $fullPath,
                  'ContentType' => mime_content_type($fullPath),
              ]);
              $ret = true;
          } catch (S3Exception $e) {
              Log::error($e->getMessage());
          }
          return $ret;
      }

      /**
      * deleteObject method
      *
      * @param string $deleteFileName
      * @return boolean
      */
      public function deleteObject($deleteFileName)
      {
          $ret = false;
          try {
              $result = $this->_s3Client->deleteObject([
                  'Bucket' => env('S3_BUCKET_NAME'),
                  'Key' => env('ITEM_IMAGE_PATH').$deleteFileName
              ]);
              $ret = true;
          } catch(S3Exception $e) {
              Log::error($e->getMessage());
          }
          return $ret;
      }
  }
  ```

  - Controller/HogeController.php
  ``` HogeController.php
  <?php
  namespace App\Controller;

  use App\Model\Utility\S3Manager;

  class HogeController extends AppController
  {
      /**
      * upload method
      **/
      public function upload()
      {
          if ($this->request->is('post') {
              $s3 = new S3Manager();
              $s3->putObject($baseDir, 'hoge.jpg', 'hoge.jpg');
          }
      }

      /**
      * delete method
      **/
      public function delete()
      {
          if ($this->request->is('post') {
              $s3 = new S3Manager();
              $s3->deleteObject('hoge.jpg');
          }
      }
  }
  ```