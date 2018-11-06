```
#include <opencv2/opencv.hpp>
#include <iostream>
#include <stdio.h>

using namespace cv;
using namespace std;

int main(int, char**)
{
	Mat frame; //동영상 파일 재생을 위한 행렬 선언
	VideoCapture cap;
	/*
	@@@@@@@@@@@@@@@@@@@@@@@@@
	VideoCapture cap(동영상 경로 , 파일);
	VideoCapture 생성자중 하나임 , 이생성자는 특정 파일을 열고 비디오 스트림을 읽기위한 생성자
	@@@@@@@@@@@@@@@@@@@@@@@@@
	*/
	// 기본 API를 사용하여 기본 카메라 열기
	cap.open(0);
	if (!cap.isOpened()) {
		cerr << "ERROR! Unable to open camera\n";
		return -1;
	}
	CascadeClassifier face_classifier;
	face_classifier.load("C:/opencv3.4.3/sources/data/haarcascades/haarcascade_frontalface_default.xml");
	cout << "Start grabbing" << endl
		<< "Press any key to terminate" << endl;
	for (; ; ) {
		bool frame_valid = true;

		try {

			// get a new frame from webcam
			cap >> frame;

		}
		catch (cv::Exception& e) {

			std::cerr << "Exception occurred. Ignoring frame... " << e.err << std::endl;
			frame_valid = false;

		}

		if (frame_valid) {
			try {
				// convert captured frame to gray scale & equalize
				cv::Mat grayframe;
				cv::cvtColor(frame, grayframe, CV_BGR2GRAY);
				cv::equalizeHist(grayframe, grayframe);

				// -------------------------------------------------------------
				// face detection routine

				// a vector array to store the face found
				std::vector<cv::Rect> faces;

				face_classifier.detectMultiScale(grayframe, faces,
					1.1, // increase search scale by 10% each pass
					3,   // merge groups of three detections
					CV_HAAR_FIND_BIGGEST_OBJECT | CV_HAAR_SCALE_IMAGE,
					cv::Size(30, 30)
				);

				// -------------------------------------------------------------
				// draw the results
				for (int i = 0; i < faces.size(); i++) {
					cv::Point lb(faces[i].x + faces[i].width, faces[i].y + faces[i].height);
					cv::Point tr(faces[i].x, faces[i].y);

					cv::rectangle(frame, lb, tr, cv::Scalar(0, 255, 0), 3, 4, 0);
				}

				// print the output
				cv::imshow("result", frame);

			}
			catch (cv::Exception& e) {
				std::cerr << "Exception occurred. Ignoring frame... " << e.err << std::endl;
			}
		}
		//사용자 Key 인터페이스
		char ch = waitKey(10);
		if (ch == 27) break; // esc 입력시 off
		if (ch == 32)//스페이스 입력시 stop
		{
			while ((ch = waitKey(10)) != 32 && ch != 27);// 스페이스가 아니거나 esc가 아니면 계속 실행
			if (ch == 27) break;//esc라면 off
		}

	}
	// VideoCapture automatically deallocate camera object
	return 0;
}

```